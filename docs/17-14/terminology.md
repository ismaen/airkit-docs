**Learn the significance of terminology commonly used in Airkit documentation.**

### [Orgs](https://support.airkit.com/docs/airkit-organizations)


Everything built within Airkit is, at the highest level, sorted into **Organizations**, or **Orgs** for short. One must have access to an **Org** in order to access Airkit.


For more on how to add users to an existing **Org**, check out [Adding Users to Airkit](https://support.airkit.com/docs/adding-users-to-airkit). For more on how to create a new **Org**, check out our [Quickstart](https://support.airkit.com/docs/quickstart).


### [The Console](https://support.airkit.com/docs/console)


The **Console** is the part of the platform that provides access to Org-level material, making it possible to configure application resources, connect external integrations, and access all applications that have been created within the relevant Org.


### [The Studio](https://support.airkit.com/docs/the-structure-of-the-studio)


The **Studio** is the interface in which your apps can be created and edited. It consists of multiple **[Builders](https://support.airkit.com/docs/introduction-to-the-builder-bar)**, each of which makes it possible to construct and edit different components of your apps.


### [Journeys](https://support.airkit.com/docs/journeys)


**Journeys** are a means of conceptualizing how Airkit keeps track of where users are within the flow of the application, as well as what they've done, entered, or requested in the process of going through it.


A **Journey** starts when a user first begins to go through the flow of an app. This can happen in a multitude of ways, but regardless of how a **Journey** starts, it spans all of the user's interactions with that app, across all relevant channels, as long as the app has some way of recognizing the Journey.


### [Actors](https://support.airkit.com/docs/actors)


Every Journey has an **Actor**. The Actor represents an individual customer going through the flow of an application. Airkit uses information associated with each actor to help route incoming chat and voice interactions to the correct customer, which enables the platform to seamlessly transition between different channels. 


### [Web Flows, Web Pages,](https://support.airkit.com/docs/web-flows) and [Web Controls](https://support.airkit.com/reference/web-controls-overview)


**Web Flows** are containers for **Web Pages**. **Web Pages** are containers for **Web Controls**, basic UI building blocks that allow users to interact with a web app.


Constructing **Web Flows** out of **Web Pages** and **Web Pages** out of **Web Controls** is how web apps are built in Airkit. This is done in the [Web Builder](https://support.airkit.com/docs/web-builder).


### [Actions](https://support.airkit.com/docs/action-builder)


**Actions** define how applications interact with users, themselves, and the outside world; a series of **Actions** taken sequentially is called an **Action Chain**. For more on **Actions**, check out [Action Builder](https://support.airkit.com/docs/action-builder).


### [Events](https://support.airkit.com/docs/airkit-events)


**Events** refer to any catalyst that might trigger an Action Chain. All Action Chains are associated with a particular **Event**. It is when – and only when – an **Event** is fired that its associated Action Chain is performed.


The different types of Airkit **Events** are:


* [**Starting Events**](https://support.airkit.com/docs/starting-events): Start an Airkit [Journey](https://support.airkit.com/docs/journeys). These Events will commonly be triggered by things like the user clicking a specific link or texting a particular number.
* [**Control Events**](https://support.airkit.com/docs/control-events): Come out of the box with each Control and vary depending on the Control's functionality. For example, [Buttons](https://support.airkit.com/reference/button-web-control) come associated with a single Event: '**Click**'. [Text Input Boxes](https://support.airkit.com/reference/text-input-web-control), on the other hand, come with three associated Events: '**On Blur**', '**Value Changed**', and '**On Enter**'.
* [**Journey Events**](https://support.airkit.com/docs/journey-events): Global Custom Events that can be invoked anywhere in a [Journey](https://support.airkit.com/docs/journeys) by the [Run Event Action](https://support.airkit.com/reference/the-run-event-action).
* [**Activity Events**](https://support.airkit.com/docs/activity-events): Activity-level Custom Events that can be invoked by the [Run Event Action](https://support.airkit.com/reference/the-run-event-action). In contrast to Journey Events, Activity Events are only accessible within a specific Activity: an individual [Web Flow](https://support.airkit.com/docs/web-flows), [Chat Bot](https://support.airkit.com/docs/chat-bot-builder), or [Voice Bot](https://support.airkit.com/docs/voice-bot-builder).
* [**App APIs & Subscription Events**](https://support.airkit.com/docs/app-api-and-subscription-events): Initiated whenever an API or subscription is triggered.


### [Data Flows](https://support.airkit.com/docs/data-flows)


**Data Flows** are custom connections. Conceptually, **Data Flows** work like functions: they take in input, process it, and return the resulting output (if applicable). 


**Data Flows** are made up of component parts called **[Data Operations](https://support.airkit.com/reference/data-operation-overview)**, which define how input is processed. They are made and edited in the [Connection Builder](https://support.airkit.com/docs/connection-builder).


### [Airscript](https://support.airkit.com/docs/airscript-quick-start)


**Airscript** is a programing language specialized for data manipulation: it's by strategically combining **Airscript** with input from app users (or other [external sources](https://support.airkit.com/docs/connecting-to-external-systems), such as an external API) that you control the order, flow, and nature of the interactions between your Airkit apps and the outside world. Most commonly, this is done by [defining a variable](https://support.airkit.com/reference/the-set-variable-action) with **Airscript** or by using **Airscript** to access or modify data via the [Transform Data Operation](https://support.airkit.com/reference/the-transform-data-operation), both of which parse any input in **Airscript** by default. To get started experimenting with Airscript, see [Testing Airscript Expressions](doc:testing-airscript-expressions) 


### [Kitcloud Templates](https://support.airkit.com/docs/kitcloud)


**KitCloud Templates** are pre-configured and customizable Airkit modules that can be used as building blocks to accelerate the development of app-building. They are available across Web Flows, voice bots, chat bots and Data Flows.