This appendix outlines the contents introduced in the process of building your first app and provides some links to more in-depth documentation. Return to this document any time you want to review the fundamentals of how to build in Airkit.


# Airkit Studio Layout


* [The Studio](https://support.airkit.com/docs/the-structure-of-the-studio)
* [The Builder Bar](https://support.airkit.com/docs/introduction-to-the-builder-bar)
* [App Preview](https://support.airkit.com/docs/app-preview)


# When you first create an app, you'll be automatically taken to [Journey Builder](https://support.airkit.com/docs/journey-builder)


In the Journey Builder, you can: 


* Connect [Kitcloud templates](https://support.airkit.com/docs/kitcloud)
* Build out complicated [user Journeys](https://support.airkit.com/docs/journeys)
* Keep track of [variables at a high-level scope](https://support.airkit.com/docs/variable-scopes)


To make a web app without the use of a Kitcloud Template:


* Indicate that your Journey starts by clicking a link
* Set the link to navigate to a [Web Flow](https://support.airkit.com/docs/web-flows)
* Create a blank Web Flow to navigate to


# To build or edit a Web Flow, navigate to [Web Builder](https://support.airkit.com/docs/web-builder)


Web Builder is where you can:


* Create and edit [Web Flows](https://support.airkit.com/docs/web-flows)
* Create and edit the [Web Pages](https://support.airkit.com/reference/navigate-to-web-page-action) that make up the [Web Flows](https://support.airkit.com/docs/web-flows)
* Create and edit [Web Controls](https://support.airkit.com/reference/web-controls-overview) on each [Web Page](https://support.airkit.com/reference/navigate-to-web-page-action).


Web Controls](https://support.airkit.com/reference/web-controls-overview) serve as small UI building blocks.


* Example [Web Controls](https://support.airkit.com/reference/web-controls-overview) include:
  * [Labels](https://support.airkit.com/reference/label-web-control)
  * [Buttons](https://support.airkit.com/reference/button-web-control)
  * [Input boxes](https://support.airkit.com/reference/text-input-web-control)
    * Input boxes can accept various various [Data Types](https://support.airkit.com/reference/data-types-overview) and [store them as variables](https://support.airkit.com/reference/the-set-variable-action)
    * (The four input boxes created for the purpose of our Contact Form accepted four instances of [Text](https://support.airkit.com/docs/working-with-text-in-airscript) input, including one in the special form [Email](https://support.airkit.com/reference/the-email-variable-data-type) and one in the special form [Phone](https://support.airkit.com/reference/the-phone-variable-data-type))


The appearance of each [Web Control](https://support.airkit.com/reference/web-controls-overview) is highly customizable.


* Modify them individually, under the "Style" section in the Inspector
* Make app-wide changes to [Variants](https://support.airkit.com/docs/working-with-themes-and-control-variants) using [Theme Builder](https://support.airkit.com/docs/styling-with-themes).


[Web Controls](https://support.airkit.com/reference/web-controls-overview) can be associated with [Events](doc:control-events) and [Actions](https://support.airkit.com/docs/action-builder).

* [Events](doc:events) trigger Action Chains, which are a set of Actions taken sequentially. 
* [Actions](https://support.airkit.com/docs/action-builder) dictate how your app will behave
  * Common Actions include:
    * Navigating to another [Web Page](https://support.airkit.com/reference/navigate-to-web-page-action)
    * Performing a custom [Data Flow](https://support.airkit.com/docs/data-flows)
      * Custom [Data Flows](https://support.airkit.com/docs/data-flows) are created in the [Connection Builder](https://support.airkit.com/docs/connection-builder), see below


# To store and structure data, use the [Data Builder](https://support.airkit.com/docs/data-builder)


The Data Builder is where you can define [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects)


* Data in [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects) can be [stored](https://support.airkit.com/docs/working-with-data) and [queried](https://support.airkit.com/docs/airdata-querying-capabilities)
* In order for the other Builders to have access to an [AirData App Object](https://support.airkit.com/docs/airdata-app-objects), its definition must be saved and migrated


# To use and modify data, use the [Connection Builder](https://support.airkit.com/docs/connection-builder)


The Connection Builder is where you can: 


* Construct custom [Data Flows](https://support.airkit.com/docs/data-flows) out of component [Data Operations](https://support.airkit.com/reference/data-operation-overview)
  * Data Flows connect the UI of your Airkit apps to other systems, be they part of Airkit (like [AirData](doc:airdata)) or not (like Salesforce).


# Frequently Asked Questions

<details>
  <summary>What is a Journey?</summary>

#### Journeys

**Journeys** are a means of conceptualizing how Airkit keeps track of where users are within the flow of the application, as well as what they've done, entered, or requested in the process of going through it.

A **Journey** starts when a user first begins to go through the flow of an app. This can happen in a multitude of ways, but regardless of how a **Journey** starts, it spans all of the user's interactions with that app, across all relevant channels, as long as the app has some way of recognizing the **Journey**.

For more on how to conceptualize Journeys in Airkit, see [Journeys](doc:journeys).

</details>


<details>
  <summary>What is AirData?</summary>

#### AirData

**AirData** is a datastore tied to an Airkit app's profile, allowing records to be stored for collection or retrieval, even after a user has closed the app or ended their [Journey](doc:journeys). Information within **AirData** is structured according to AirData App Objects. For more information on how data is structured in **AirData**, see documentation on [AirData App Objects](doc:airdata-app-objects).

Once stored in **AirData**, information can be used or analyzed in a variety of ways, both outside and within Airkit apps. The article [AirData Querying Capabilities](doc:airdata-querying-capabilities) dives deeper into how to access information stored in **AirData**.

</details>

<details>
  <summary>What is a Web Flow?</summary>

#### Web Flows

**Web Flows** are containers for Web Pages. A user's Journey will frequently consist of multiple Web Pages, which will be sorted into **Web Flows**. Each **Web Flow** is typically built around a particular purpose, such as collecting a user's contact information.

Because the application being made in this tutorial is, by design, very simple, it consists of only a single **Web Flow**. However, Airkit applications can consist of any number of **Web Flows**, and when building out long, complicated Journeys, properly designated **Web Flows** are an important component of keeping app components organized.

The article [Web Flows](doc:web-flows) goes into more depth on what **Web Flows** are and how they are used.

</details>

<details>
  <summary>What are Web Controls?</summary>

#### Web Controls

**Web Controls** are basic UI building blocks that allow users to interact with a web app. They’re things like [Buttons](ref:button-web-control), [input boxes](ref:text-input-web-control), and [Progress Bars](ref:progress-bar-web-control). Much like how Web Pages are the component parts of Web Flows, **Web Controls** are the component parts of Web Pages.

Each **Web Control** is different, because each component part of a Web Page must interact with users in a different way. [Labels](ref:label-web-control), for instance, only need to be read, where as [Text Input Boxes](ref:text-input-web-control) must be able to bind user input to a variable that can be called on at some point downstream. 

All **Web Controls**: 

* Effect the current page UI or functionality. (Most are visual but some act as containers or add invisible functionality to the web application.)
* Use properties to control their style and behavior.
* Are constructed in a "tree" structure that allows controls to contain children controls but always roll up to the page at the top level.

For a deeper dive into individual **Web Controls**, see [the associated reference documents](ref:web-controls-overview).

</details>

<details>
  <summary>What is the difference between a Text Input Control, a Phone Input Control, and an Email Input Control?</summary>

#### Built-in validation

The Text Input Control, Phone Input Control, and Email Input Control all accept [strings](ref:the-text-variable-data-type) as user input. (In Airkit, both [Phone](ref:the-phone-variable-data-type) and [Email](doc:email) types are subcategories of Text.) However, while the Text Input Control accepts any and all strings as valid input and binds them to the associated variable, the Phone and Email Input Controls first run a test to confirm that the string the user gave was a properly-formatted phone number or email (respectively) before binding the input to the associated variable. If the string the user gave was not properly formatted, the associated variable will remain ```NULL```. 

Note that while this built-in validation process prevents your Airkit apps from saving inappropriately-formatted data, it does not automatically communicate any part of this validation process to users. If you want to include intuitive error messages in your applications, you can construct them according to the process outlined in [Validation of Forms and User Data](doc:validation-of-forms-and-user-data).    

</details>

<details>
  <summary>What does it mean for a phone number or email to be properly formatted?</summary>

<br>

Airkit defines the Phone and Email data types so that they must fulfill certain criteria. For instance, a Phone must contain a country code as well as the appropriate number of digits, while an Email must contain the '@' symbol followed by a domain name that includes a recognized top-level domain.

Under the hood, the Phone Input Control uses the [ISPHONE](ref:isphone) function to test if a user has given a valid Phone data type, and the Email Input Control uses the [ISEMAIL](ref:isemail) function to test if a user has given a valid Email data type. See function documentation for more details on what the Phone and Email Input Controls will accept as valid.

</details>

<details>
  <summary>What is a Variant?</summary>

#### Variants

A **Variant** is a set of styling properties for a specific Web Control, similar to a class in CSS. If you're not familiar with CSS classes, you might compare Web Controls and Variants to dinnerware. Plates, cups, and forks are all like different web controls: they each have a particular function, and this is reflected in aspects of their appearance. However, not all plates look the same. A square red plate and a round blue plate are both capable of serving as plates and are simply styled differently. If you are deciding whether to set your table with your blue plates or your red plates, this is like choosing between different **Variants** of plates.

Every Web Control has associated **Variants**: cosmetic variations that appear differently but function identically. **Variants** can be edited in [Theme Builder](https://support.airkit.com/docs/theme-builder) and then used as defaults when adding new Web Controls. For instance, within a single application, you might create two **Variants** of button: a rectangular one in red, and a round one in blue. Any changes made to existing **Variants** also apply retroactively: existing Web Controls previously styled according to the old default will immediately take the form specified by the new default. This allows for consistent branding throughout the entirety of each user's Journey, and it also makes it easy to see how different combinations of colors, fonts, and graphics look together. 

</details>

<details>
  <summary>What is a Data Flow?</summary>

#### Data Flows

**Data Flows** are custom connections. Conceptually, **Data Flows** work like functions: they take in input, process it, and return the resulting output (if applicable). **Data Flows** are primarily used to connect the front-end of Airkit apps to back-end systems, be they are part of Airkit (such as AirData) or external (such as Salesforce). Any data processing that must occur in order to make these connections smoothly will also be done within a **Data Flow**. For instance, if an API request returns a JSON object from which only a single attribute is worth displaying to the app user, it is within a **Data Flow** that the relevant information will be isolated. 


For a deeper discussion on **Data Flows**, see [this article](https://support.airkit.com/docs/data-flows). For more information on the different kinds of Data Operations available, see the [Data Operations Overview](https://support.airkit.com/reference/data-operation-overview).

</details>

<details>
  <summary>Why create a Data Flow to send information to AirData if it has already been bound to a variable?</summary>

#### Working with Data

When a value is bound to a variable, that value is tied to an individual [Journey](doc:journeys). This simplifies the process of keeping track of information in the short term. If our contact form becomes published, and both Alice and Bob fill it out at the same time, the value of **name_input** will be different in Alice's Journey than in Bob's. Airkit will handle the details of keeping them separate.

However, outside of any Journey, we, the app builders, might want to access certain information collected from all uses of our application. Upon sending out a Contact Form, for instance, we will likely want to be able to access information submitted by everyone, on every Journey, and thus we want to collect all relevant information in one easily-accessible place: AirData. (Note that while, in the case of creating a simple Contact Form, all bound variables are relevant, this will not always be the case. AirData App Objects are customizable precisely so that builders can store information in the way that is most conducive to their use case, rather than being bogged down by automatically-collected but ultimately cumbersome data.)

For a deeper diving into how data is conceptualized in Airkit as well as the crucial difference between binding data to a variable and saving it to AirData, check out [Working with Data](doc:working-with-data).

</details>

<details>
  <summary>What is an Action Chain?</summary>

#### Actions

An **Action Chain** is a series of Actions taken sequentially.

**Actions** are a broad category. They can be do everything from [run a Data Flow](ref:the-run-data-flow-action) to [create a timer](ref:the-create-timer-action). There's also the [Condition](ref:the-condition-action) Action, which makes it possible to create branching **Action Chains**, where different **Actions** are taken depending on whether or not certain conditions are met.

For more on how to created an **Action Chain**, see [Action Builder](doc:action-builder), which is where **Action Chains** are defined. For more on the different kinds of **Actions** that can be taken, see [the reference documentation](ref:analytics-identify-action) 

</details>

</details>

<details>
  <summary>What are Airkit Events?</summary>

#### Airkit Events

In the context of the Airkit platform, **Events** refer to any catalyst that might trigger an [Action Chain](https://support.airkit.com/docs/action-builder). All Action Chains are associated with a particular **Event**. It is when – and only when – an **Event** is fired that its associated Action Chain is performed.

At its core, an **Event** is a piece of information that tells the platform something happened and might include optional metadata about the Actions that will consequently be taken. Not all **Events** will be associated with an Action Chain. An **Event** merely signals that the platform must check and see if there are any Actions to take. In this way, an **Event** like a letter: it's sent from somewhere, but ultimately once it gets to the recipient, the recipient decides what they do with it. The letter might spur some action, or it might be thrown directly in the trash.

When we say that **Events** tell the platform "something happened," we are being deliberately vague. All kind of things might trigger **Events**. A user clicking a [Button Web Control](https://support.airkit.com/reference/button-web-control) is an **Event**, as is the [instance before sending an SMS message](https://support.airkit.com/reference/decision-menu-control), as is updating a [Web Flow](https://support.airkit.com/docs/web-flows).

</details>