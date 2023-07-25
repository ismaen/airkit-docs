An **Actor** represents someone who goes on an Airkit Journey. Put another way, any individual who goes through an application flow is represented by an **Actor**.

While the fundamental definition of an **Actor** is straightforward, the concept of an **Actor** has deep implications regarding what sort of interactions are allowed to fall under the umbrella of a single Journey. Without a way to recognize the users embarking on Journeys, there would be no way to communicate with them across multiple channels. Identifying the **Actor** is what allows Airkit to support omni-channel Journeys.

# Identifying an Actor

**Actors** are identified by their phone numbers. Defining phone numbers as unique identifiers for each **Actor** requires making the following assumptions:

* Each user has only a single phone number that they will use to interact with your application.
* Each user has exclusive use of their phone number. No two users will interact with an application using the same phone number.
* Every phone number has the capacity to call, text, and browse the web.

Identifying **Actors** by their associated phone numbers paves the way to incorporate call and text channels into a Journey.

Identifying **Actors** by phone number means that, while every Journey has an **Actor**, not every **Actor** has an identifier. Journeys are tracked directly within the Airkit platform, and so it is useful to assign an automatically-generated identifier to each one. **Actors** are people (or, at least, **Actors** are simplified digital representations of people) that exist outside of the Airkit platform, and so they must be identified by their own intrinsic properties.

# Properties of the Actor Namespace

Out of the box, **Actors** are structured such that the Actor Namespace has the following properties:

* **first_name** *([string](ref:the-text-variable-data-type))* - the **Actor's** first name.
* **last_name** *(string)* - the **Actor's** last name.
* **full_name** *(string)* - the **Actor's **full name.
* **email** *(string)* - the **Actor's** email. 
* **phone** *(string)* - the **Actor's** phone number. This serves as a unique identifier.
* **timezone** *(string)* - the **Actor's** timezone.

These properties correspond to the properties associated with the  ```Identity``` object. Editing the properties of the ```Identity``` object within [Data Builder](doc:data-builder) will modify the structure of the **Actor** accordingly. 

Note that these properties are all tied to an **Actor**, but that they cannot all be used as identifiers, because they are not all reliably unique.

Note also that while the *structure* of the Actor Namespace is set automatically, the properties will be blank by default, and each one must be set explicitly. Values of each **Actor** property can be assigned using the [Set Variable](ref:the-set-variable-action) Action just like any other variable. 

Use dot notation when referencing a property within the Actor Namespace. For instance, to reference the Actor's phone number, access ```actor.phone``` wherever Airscript is accepted. (See [Airscript Quick Start](doc:airscript-quick-start) for more details). The Actor Namespace is available at any point throughout a Journey. 

# Initializing an Actor

Variables saved in the Actor Namespace are just that: locally-stored variables. They do not automatically establish communication channels any more than other locally-stored variables do.

In order to automatically parse and establish communication channels, relevant **Actor** properties must be copied into Airkit's actor_internal database. This is what allows Airkit to send outgoing messages through the correct channels as well as automatically associate incoming messages with the relevant Journey. Note that it is not possible to directly access data in actor_internal from the Airkit platform.

Copying **Actor** properties into actor_internal is called Initializing an **Actor**, and it is done via the [Initialize Actor](ref:the-initialize-actor-action) Action.

The diagram below represents a Journey after relevant **Actor** properties have been set and right before an **Actor** is initialized.

<img src="./assets_v1714/actors-v1714-0.png" alt="organizing info" style="max-width: 500px; width:100%"/>

This next diagram represents what happens when the **Actor** is initialized. Whatever is stored in the Actor Namespace gets copied to airkit_internal. 

<img src="./assets_v1714/actors-v1714-1.png" alt="organizing info" style="max-width: 500px; width:100%"/>

Once an **Actor** is initialized, relevant communication channels will be established automatically. For instance, once an **Actor** is initialized with ```actor.phone```, all of their incoming texts will be considered part of their Journey, and all outgoing phone calls will be sent to their phone number.