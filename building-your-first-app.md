We recommend building a simple Contact Form as your first application, and we've provided a tutorial for doing so in two mediums: a video and a written tutorial, both of which cover the same material. Feel free to go through both, to use either exclusively, or to supplement one with the other – whatever is most conducive to your learning style.

<details>
  <summary>Why start with a simple Contact Form?</summary>

####Broader Context  

Airkit provides a variety of tools that make it possible to build complicated apps very quickly. Among these tools is the [Airkit Studio](https://support.airkit.com/docs/studio), the interface in which every detail of your apps can be created and edited, and [KitCloud](https://support.airkit.com/docs/kitcloud), which supplies a multitude of pre-configured templates.


It's possible for most KitCloud templates to function as self-contained (if extremely simple and decontextualized) applications on their own. For instance, there are templates to gather and record customer information, templates to accept payments, and templates to verify a user's phone number. By having much of the skeleton for these common use cases already pre-built, creating complicated app flows takes very little time at all: KitCloud templates can be used as foundational building blocks, which can then be connected and edited in Airkit Studio as needed. Your final apps might be any combination of KitCloud templates, custom app flows, and even templates you yourself designed for the purpose of re-using.


As you might imagine, building out long, intricate [user Journeys](https://support.airkit.com/docs/journeys) can become very complicated very quickly, so when getting started, it's best to peel away some of the layers of abstraction. Building a simple Contact Form provides a digestible introduction to the component parts can make up these Journeys.


As it happens, KitCloud comes with a template that has this exact form pre-built; in addition to building your first app, you're also be replicating a template. Building a simple form provides an introduction not only into what goes into getting an app off the ground, but also how templates work under the hood.
</details>

# How to Build a Contact Form Video

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FAoRcjWC5Q4Q%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAoRcjWC5Q4Q&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FAoRcjWC5Q4Q%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=AoRcjWC5Q4Q",
  "title": "Airkit 101 - Build Your First App in 10 Minutes",
  "favicon": "https://www.youtube.com/s/desktop/15c06292/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/AoRcjWC5Q4Q/hqdefault.jpg"
}
[/block]
# How to Build a Contact Form Tutorial

Here, we'll cover how to build a Contact Form app from scratch. The app will guide users on a **Journey** that captures their contact info and then store that information back to AirData.

<details>
  <summary>What is a Journey?</summary>

#### Journeys

**Journeys** are a means of conceptualizing how Airkit keeps track of where users are within the flow of the application, as well as what they've done, entered, or requested in the process of going through it.

An Airkit **Journey** starts when a user first begins to go through the flow of an app. This can happen in a multitude of ways, but regardless of how a **Journey** starts, it spans all of the user's interactions with that app, across all relevant channels, as long as the app has some way of recognizing the **Journey**.

For more on how to conceptualize Journeys in Airkit, see [Journeys](doc:journeys).

</details>


<details>
  <summary>What is AirData?</summary>

####AirData

**AirData** is a datastore tied to an Airkit app's profile, allowing records to be stored for collection or retrieval, even after a user has closed the app or ended their [Journey](doc:journeys). Information within **AirData** is structured according to AirData App Objects, such as the ** Contact** Object described later in this tutorial. For more information on how data is structured in **AirData**, see documentation on [AirData App Objects](doc:airdata-app-objects).

Once stored in **AirData**, information can be used or analyzed in a variety of ways, both outside and within Airkit apps. [AirData Querying Capabilities](doc:airdata-querying-capabilities) dives deeper into how to access information stored in **AirData**.

</details>

#### These are the Studio parts you will be working with:

* [Journey Builder](doc:journey-builder): Start the Journey
* [Web Builder](https://support.airkit.com/docs/web-builder): Creating the Contact Form UI
* [Data Builder](https://support.airkit.com/docs/data-builder): Creating the App Object in AirData
* [Connection Builder](https://support.airkit.com/docs/connection-builder): 
    * Creating the Data Flow to Insert Data
    * Connecting the Data Flow to the UI
* [App Preview](https://support.airkit.com/docs/app-preview): Previewing the App


Creating the Contact Form
-------------------------


When creating an app, you will first land on [Journey Builder](https://support.airkit.com/docs/journey-builder) in the Studio. This is where the app’s Journey is created by choosing a Starting Event. 


1. Since the Contact Form app will be triggered by a link, select **Clicks a link**.


![1red.png](./assets_v1714/building-your-first-app-v1714-0.png)


2. Click on the '+' icon next to the starting point to add the action that will occur when users click on that link. Among the many options, look for the **Navigate to Web Flow** Action. 


![2red.png](./assets_v1714/building-your-first-app-v1714-1.png)


3. You will be prompted to select which Web Flow to Navigate to. Since the app doesn’t have any Web Flows yet, add one by clicking on **Add Web Flow**.


![3red.png](./assets_v1714/building-your-first-app-v1714-2.png)


To build the Web Flow, you can double click on the added Web Flow or toggle over to Web Builder, where the UI for the application is actually built.

<details>
  <summary>What is a Web Flow?</summary>

#### Web Flows

**Web Flows** are containers for Web Pages. A user's Journey will frequently consist of multiple Web Pages, which will be sorted into **Web Flows**. Each **Web Flow** is typically built around a particular purpose, such as collecting a user's contact information.

Because the application being made in this tutorial is, by design, very simple, it consists of only a single **Web Flow**. However, Airkit applications can consist of any number of **Web Flows**, and when building out long, complicated Journeys, properly designated **Web Flows** are an important component of keeping app components organized.

The article [Web Flows](doc:web-flows) goes into more depth on what **Web Flows** are and how they are used.

</details>

The Contact Form Web Flow will include two Web Pages: A Contact Info Web Page and a Thank You Web Page.


### Building the Contact Info Web Page


1. In [Web Builder](https://support.airkit.com/docs/web-builder), double click on the recently added Web Flow to rename it and click on the '+' icon next to it to add the first Web Page. Double click on it to edit the name for a more descriptive one.


![4red.png](./assets_v1714/building-your-first-app-v1714-3.png)


2. Click on the '+' icon next to the Web Page to add the Web Controls one by one. There are different types of Controls, each serving a specific purpose. 


![5.png](./assets_v1714/building-your-first-app-v1714-4.png)

<details>
  <summary>What are **Web Controls**?</summary>

#### Web Controls

**Web Controls** are basic UI building blocks that allow users to interact with a web app. They’re things like [Buttons](ref:button-web-control), [input boxes](ref:text-input-web-control), and [Progress Bars](ref:progress-bar-web-control). Much like how Web Pages are the component parts of Web Flows, **Web Controls** are the component parts of Web Pages.

Each **Web Control** is different, because each component part of a Web Page must interact with users in a different way. [Labels](ref:label-web-control), for instance, only need to be read, where as [Text Input Boxes](ref:text-input-web-control) must be able to bind user input to a variable that can be called on at some point downstream. 

All **Web Controls**: 

* Effect the current page UI or functionality. (Most are visual but some act as containers or add invisible functionality to the web application.)
* Use properties to control their style and behavior.
* Are constructed in a "tree" structure that allows controls to contain children controls but always roll up to the page at the top level.

For a deeper dive into individual **Web Controls**, see [the associated reference documents](ref:web-controls-overview).

</details>

This Contact Form includes Input Controls, that is, fields the users will later complete. The Input Controls on this Form are the following: Name, Phone, Email and Company. Hence, choose the [Text Input](https://support.airkit.com/reference/text-input-web-control) Control for the “Name” and "Company" fields, as users are expected to enter a text; choose the [Phone Input](https://support.airkit.com/reference/phone-input-web-control) Control for the “Phone” field, as users are expected to enter numbers following a phone format; and choose the [Email Input](ref:email-input-web-control) Control for the "Email" field. 

![5PUNTO9.png](./assets_v1714/building-your-first-app-v1714-5.png)


<details>
  <summary>What is the difference between a Text Input Control, a Phone Input Control, and an Email Input Control?</summary>

#### Built-in validation

The Text Input Control, Phone Input Control, and Email Input Control all accept [strings](ref:the-text-variable-data-type) as user input. (In Airkit, both [Phone](ref:the-phone-variable-data-type) and [Email](doc:email) types are subcategories of Text.) However, while the Text Input Control accepts any and all strings as valid input and binds them to the associated variable, the Phone and Email Input Controls first run a test to confirm that the string the user gave was a properly-formatted phone number or email (respectively) before binding the input to the associated variable. If the string the user gave was not properly formatted, the associated variable will remain ```NULL```. 

<details>
  <summary>What does it mean for a phone number or email to be properly formatted?</summary>

<br>

Airkit defines the Phone and Email data types so that they must fulfill certain criteria. For instance, a Phone must contain a country code as well as the appropriate number of digits, while an Email must contain the '@' symbol followed by a domain name that includes a recognized top-level domain.

Under the hood, the Phone Input Control uses the [ISPHONE](ref:isphone) function to test if a user has given a valid Phone data type, and the Email Input Control uses the [ISEMAIL](ref:isemail) function to test if a user has given a valid Email data type. See function documentation for more details on what the Phone and Email Input Controls will accept as valid.

</details>

<br>

Note that while this built-in validation process prevents your Airkit apps from saving inappropriately-formatted data, it does not automatically communicate any part of this validation process to users. If you want to include intuitive error messages in your applications, construct them according to the process outlined in [Validation of Forms and User Data](doc:validation-of-forms-and-user-data).    

</details>



For each Input Control, a [Variable](https://support.airkit.com/docs/variable-scopes) is automatically created and binded to the Value of that input.


![6red.png](./assets_v1714/building-your-first-app-v1714-6.png)


3. Once the Controls are added, include a [Label Control](https://support.airkit.com/reference/label-web-control) above each of them to show the user what input they are filling out. 


![7.png](./assets_v1714/building-your-first-app-v1714-7.png)


To edit the Label, double click on it in the Stage or change the Text property in the Inspector section. You can also change the style of the Label by choosing a Variant.

<details>
  <summary>What is a Variant?</summary>

#### Variants

A **Variant** is a set of styling properties for a specific Web Control, similar to a class in CSS. If you're not familiar with CSS classes, you might compare Web Controls and Variants to dinnerware. Plates, cups, and forks are all like different web controls: they each have a particular function, and this is reflected in aspects of their appearance. However, not all plates look the same. A square red plate and a round blue plate are both capable of serving as plates and are simply styled differently. If you are deciding whether to set your table with your blue plates or your red plates, this is like choosing between different **Variants** of plates.

Every Web Control has associated **Variants**: cosmetic variations that appear differently but function identically. **Variants** can be edited in [Theme Builder](https://support.airkit.com/docs/theme-builder) and then used as defaults when adding new Web Controls. For instance, within a single application, you might create two **Variants** of button: a rectangular one in red, and a round one in blue. Any changes made to existing **Variants** also apply retroactively: existing Web Controls previously styled according to the old default will immediately take the form specified by the new default. This allows for consistent branding throughout the entirety of each user's Journey, and it also makes it easy to see how different combinations of colors, fonts, and graphics look together. 

</details>


![8.png](./assets_v1714/building-your-first-app-v1714-8.png)


4. Finally, add a [Button Control](https://support.airkit.com/reference/button-web-control). This will be later used to submit data collected from users to AirData.


![9button.png](./assets_v1714/building-your-first-app-v1714-9.png)


Edit the name by double clicking on it or from the Text in the Inspector section.


![10buttonred.png](./assets_v1714/building-your-first-app-v1714-10.png)


5. Now that the Form is ready, click on the Web Page to check all the auto-created Variables that will store the input Values. If necessary, rename the Variables so they are easy to identify. For example, change **text_input** to **name_input.**


![11variableswebpage.png](./assets_v1714/building-your-first-app-v1714-11.png)


### Building the Thank You Page


Add a Thank You Web Page to the Web Flow for users to see after completing the Form.


1. Click on the '+' icon next to the Web Flow and add the second Web Page. Double click on it to edit the name for a more descriptive one. 


![12thankyou.png](./assets_v1714/building-your-first-app-v1714-12.png)


2. Click on the '+' icon next to the new Web Page to add the Label Control.


![13.png](./assets_v1714/building-your-first-app-v1714-13.png)


3. Type the message users will see on submitting the Form by editing the Label.


![14.png](./assets_v1714/building-your-first-app-v1714-14.png)


Creating the App Object in AirData
----------------------------------

To save the information in the app, an [App Object](https://support.airkit.com/docs/airdata-app-objects) has to be built in [Data Builder](https://support.airkit.com/docs/data-builder).


1. From Data Builder, click on the '+' icon next to Datastore and select Add App Object.


![15AppObject.png](./assets_v1714/building-your-first-app-v1714-15.png)


2. Click on the '+' icon next to the recently added object and include the fields that you need. In this case, it’s going to be a Text type, for the name and company fields; a Phone type for the phone number; and an Email type for the email address. 


<img src="./assets_v1714/building-your-first-app-v1714-16.png" alt="organizing info" style="max-width: 350px; width:100%"/>


3. Double click on the App Object as well as on the fields to rename them. We recommend using lower case. 

<img src="./assets_v1714/building-your-first-app-v1714-17.png" alt="organizing info" style="max-width: 350px; width:100%"/>


4. Finally, save the app to run a migration and create the AirData Table where the information will be saved later on.


![16.5.png](./assets_v1714/building-your-first-app-v1714-18.png)  



Creating the Data Flow to Insert Data
-------------------------------------


A [Data Flow](https://support.airkit.com/docs/data-flows) has to be created from [Connection Builder](https://support.airkit.com/docs/connection-builder) to send the data back to [AirData](https://support.airkit.com/docs/airdata).


<details>
  <summary>What is a Data Flow?</summary>

#### Data Flows

**Data Flows** are custom connections. Conceptually, **Data Flows** work like functions: they take in input, process it, and return the resulting output (if applicable). **Data Flows** are primarily used to connect the front-end of Airkit apps to back-end systems, be they are part of Airkit (such as AirData) or external (such as Salesforce). Any data processing that must occur in order to make these connections smoothly will also be done within a **Data Flow**. For instance, if an API request returns a JSON object from which only a single attribute is worth displaying to the app user, it is within a **Data Flow** that the relevant information will be isolated. 


For a deeper discussion on **Data Flows**, see [Data Flows](https://support.airkit.com/docs/data-flows). For more information on the different kinds of Data Operations available, see the [Data Operations Overview](https://support.airkit.com/reference/data-operation-overview).

</details>

<details>
  <summary>Why create a Data Flow to send information to AirData when it has already been bound to a variable?</summary>

####Working with Data

When a value is bound to a variable, that value is tied to an individual [Journey](doc:journeys). This simplifies the process of keeping track of information in the short term. If our contact form becomes published, and both Alice and Bob fill it out at the same time, the value of **name_input** will be different in Alice's Journey than in Bob's. Airkit will handle the details of keeping them separate.

However, outside of any Journey, we, the app builders, might want to access certain information collected from all uses of our application. Upon sending out a Contact Form, for instance, we will likely want to be able to access information submitted by everyone, on every Journey, and thus we want to collect all relevant information in one easily-accessible place: AirData. (Note that while, in the case of creating a simple Contact Form, all bound variables are relevant, this will not always be the case. AirData App Objects are customizable precisely so that builders can store information in the way that is most conducive to their use case, rather than being bogged down by automatically-collected but ultimately cumbersome data.)

For a deeper diving into how data is conceptualized in Airkit as well as the crucial difference between binding data to a variable and saving it to AirData, check out [Working with Data](doc:working-with-data).

</details>


1. From Connection Builder, click on the '+' icon next to Data Flow and then on Create Blank to add a new Data Flow.


![18DataFlowNew.png](./assets_v1714/building-your-first-app-v1714-19.png)


2. Once added, double click on it to rename it.


![19.png](./assets_v1714/building-your-first-app-v1714-20.png)


3. In the Inspector section, add the Inputs that will enable you to pass the Values from the Form Inputs to the Data Flow and back to AirData. When all data types display, select the Text input and rename it to “name”; select the Phone input and rename it to “phone” and do the same with the other two fields. 


![20red.png](./assets_v1714/building-your-first-app-v1714-21.png)  



4. Add an AirData Request Data Operation by clicking on '+' the icon in the Stage.


![22red.png](./assets_v1714/building-your-first-app-v1714-22.png)


5. Inside the AirData Request, choose from the dropdown the App Object that will save the information and select INSERT as the Type of operation to perform since it allows adding an item into AirData. 

<img src="./assets_v1714/building-your-first-app-v1714-23.png" alt="organizing info" style="max-width: 300px; width:100%"/>


6. Since AirData expects a full JSON object to pass in, create the “Contact” object inline. You can check out the schema from the sample data of the App Object, by going to the Start step and adding the Contact Object as a Variable.


![24red.png](./assets_v1714/building-your-first-app-v1714-24.png)


Then, copy the schema from the Variable tab:


![25red.png](./assets_v1714/building-your-first-app-v1714-25.png)


7. Go back to the AirData Request step and paste the schema to adjust the sample text to the Inputs. Hence, replace “Sample Text” with the “name” input; the phone number with the “phone” input; and so on.

<img src="./assets_v1714/building-your-first-app-v1714-26.png" alt="organizing info" style="max-width: 300px; width:100%"/>

8. To test the Data Flow and make sure it is sending the information back to AirData, go to the Run Results section and click on Run. A “Successfully run step” message should pop up.

<img src="./assets_v1714/building-your-first-app-v1714-27.png" alt="organizing info" style="max-width: 300px; width:100%"/>


Save the application and go to Data Builder to check if the data was inserted.


Connecting the Data Flow to the UI
----------------------------------


Now that the Data Flow is working and sending data to Data Builder, go back to Web Builder to connect the operation to the UI. In Web Builder, you can define the Action Chain to be run when the users click on “Submit” once they finish completing their Form. This Action Chain is triggered by the Airkit Event of a user clicking the button.

<details>
  <summary>What is an Action Chain?</summary>

#### Actions

An **Action Chain** is a series of **Actions** taken sequentially.

**Actions** are a broad category. They can be do everything from [run a Data Flow](ref:the-run-data-flow-action) to [navigate to a specific Web Page](ref:navigate-to-web-page-action) to [create a timer](ref:the-create-timer-action). There's also the [Condition](ref:the-condition-action) Action, which makes it possible to create branching **Action Chains**, where different **Actions** are taken depending on whether or not certain conditions are met.

For more on how to created an **Action Chain**, see documentation on [Action Builder](doc:action-builder), which is where **Action Chains **are defined. For more on the different kinds of **Actions** that can be taken, see [the reference documentation](ref:analytics-identify-action) 

</details>

<details>
  <summary>What are Airkit Events?</summary>

#### Airkit Events

In the context of the Airkit platform, **Events** refer to any catalyst that might trigger an [Action Chain](https://support.airkit.com/docs/action-builder). All Action Chains are associated with a particular **Event**. It is when – and only when – an **Event** is fired that its associated Action Chain is performed.

At its core, an Airkit **Event** is a piece of information that tells the platform something happened and might include optional metadata about the Actions that will consequently be taken. Not all **Events** will be associated with an Action Chain. An Event **merely** signals that the platform must check and see if there are any Actions to take. In this way, an **Event** like a letter: it's sent from somewhere, but ultimately once it gets to the recipient, the recipient decides what they do with it. The letter might spur some action, or it might be thrown directly in the trash.

When we say that **Events** tell the platform "something happened," we are being deliberately vague. All kind of things might trigger **Events**. A user clicking a [Button Web Control](https://support.airkit.com/reference/button-web-control) is an **Event**, as is the [instance before sending an SMS message](https://support.airkit.com/reference/decision-menu-control), as is updating a [Web Flow](https://support.airkit.com/docs/web-flows).

There are many different types of Airkit **Events**, including [Starting Events](doc:starting-events), one of which you've already created in the [Journey Builder](doc:journey-builder), and [Control Events](doc:control-events), including the 'Clicked' Event associated with all [Button Web Controls](ref:button-web-control).

</details>



1. Click on the “Submit” button and go to the Actions tab in the Inspector.



![28.png](./assets_v1714/building-your-first-app-v1714-28.png)


2. Click on the '+' icon for the Actions menu to display and select Run Data Flow from the Data Options.


![29.png](./assets_v1714/building-your-first-app-v1714-29.png)


3. Pick the previously created Data Flow and complete the displayed Inputs with the Input Variables of the Web Page. They will be suggested as you type:


![31.png](./assets_v1714/building-your-first-app-v1714-30.png)


4. Repeat the process to add an action to the button and this time select the Navigate to Web Page action. Choose the Thank You Web Page so that users are directed there when clicking on the button.


![32red.png](./assets_v1714/building-your-first-app-v1714-31.png)


Save the app and it will be ready to be tested.


Previewing the App
------------------


Once the app is all set, it can be tested in the App Preview.


1. Click on Preview at the right-hand corner of the Studio, which will open a new tab.


![33red.png](./assets_v1714/building-your-first-app-v1714-32.png)


2. Click on the globe icon, which allows the app to be launched from the start.


![34red.png](./assets_v1714/building-your-first-app-v1714-33.png)


3. Complete the fields and click on “Submit”.


![35red.png](./assets_v1714/building-your-first-app-v1714-34.png)


As expected, it will take the user to the Thank You Web Page.


![36.png](./assets_v1714/building-your-first-app-v1714-35.png)


4. Finally, go back to Data Builder and check if the entered information has been saved into AirData:


![37fake.png](./assets_v1714/building-your-first-app-v1714-36.png)


Now the application is ready to be published.