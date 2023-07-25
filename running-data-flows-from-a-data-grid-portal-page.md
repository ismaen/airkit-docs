[Data Grid Portal Pages](https://support.airkit.com/docs/portal-data-grids) make it easy for [Portal](https://support.airkit.com/docs/portal-capabilities) users to interact with said [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects) in various pre-approved ways. One of the most powerful ways Portal viewers can interact with data in a Data Grid is by running [Data Flows](https://support.airkit.com/docs/data-flows) on select App Object instances. 


# Prerequisites: [App Object](https://support.airkit.com/docs/airdata-app-objects-AirData-App-Objects) and  [Portal Data Grids](https://support.airkit.com/docs/portal-data-grids) pages


In order to run a [Data Flow](https://support.airkit.com/docs/data-flows) on App Objects displayed in a Data Grid Portal Page, you must first have access to both an App Object and a Data Grid Portal Page that displays said App Object.


## Creating an App Object


App Objects are defined in the [Data Builder](https://support.airkit.com/docs/data-builder). There are no constraints to the type of App Object you need to create here: they can have any number of properties, which themselves might be any [primitive type](https://support.airkit.com/reference/data-types-overview) or even other App Objects. Once the structure of an App Object has been fully described, make sure to save your application so that the rest of the application will have access to the App Object you just defined.


For a deeper dive into how to create App Objects and how they might connect to they rest of your application, check out [AK101](https://support.airkit.com/docs/building-your-first-app). 


## Creating a Data Grid Portal Page


A [Data Grid Portal Page](https://support.airkit.com/docs/portal-data-grids) displays a table of data stored in [AirData](https://support.airkit.com/docs/airdata); each Data Grid must be associated with a particular App Object. You can select which App Object you want your Data Grid to display from a dropdown menu in the [Inspector](https://support.airkit.com/docs/portal-builder). Select the App Object you intend to display and run [Data Flows](https://support.airkit.com/docs/data-flows) on.


For more on how to create a Data Grid Portal Page that displays a particular App Object, check out the documentation on [Portal Builder](https://support.airkit.com/docs/portal-builder). 


# Step 1: Build out your Data Flow


[Data Flows](https://support.airkit.com/docs/data-flows) that can be run through a Data Grid Portal Page are built out in the same way as any other Data Flow: in the [Connection Builder](https://support.airkit.com/docs/connection-builder), using all the same [Data Operations](https://support.airkit.com/reference/data-operation-overview).


There are only two constraints to keep in mind while constructing Data Flows intended run from a Data Grid.


Firstly, when a Data Flow is run from a Data Grid, there is no designated place for resulting output to be displayed. Data Flows that are run from a Data Grid are intended to take actions – [send emails](https://support.airkit.com/docs/sending-email-from-airkit), update a database, activate [Chat Bots](https://support.airkit.com/docs/building-a-simple-chat-bot) – not return output. While the Portal Builder does not forbid incorporating a Data Flow that returns some output, it must be understood that whatever output it returns will not, in practice, be accessible. If you want to run a Data Flow that displays new information within a Data Grid, it is necessary to build a place for that desired information within the displayed App Object and then run an [Airdata query](https://support.airkit.com/docs/airdata-querying-capabilities) as part of the incorporated Data Flow.


Secondly, the input required by the Data Flow must be structured appropriately. Once a Data Flow is built into a Portal Page, it can only be fed input in the form of selected App Object instances, and the structure of the Data Flow being run must reflect that.


This means that the Data Flow can only accept input structured in two ways:


1. The App Object that is being displayed in the Data Grid
2. A [List](https://support.airkit.com/reference/the-list-data-type) of said App Objects


## Brief Tangent: How Data Flows incorporated into a Data Grid parse input


The above section specified that a [Data Flow](https://support.airkit.com/docs/data-flows) created to run from a Data Grid Portal Page can accept input in two forms: a singular [App Object](https://support.airkit.com/docs/airdata-app-objects-AirData-App-Objects), or a singular [List](https://support.airkit.com/reference/the-list-data-type) of App Objects (when, in both cases, all pertinent App Objects match the App Object being displayed in the Data Grid).


Note that App Object instances are selected by clicking on the check box to immediate left of the row that displays the desired instance:


![2021-08-09_16-38-07__2_.gif](./assets_v1714/running-data-flows-from-a-data-grid-portal-page-v1714-0).gif)


However, while input is always given in this way, how the input is parsed depends on the format of input accepted by the Data Flow.


**When a Data Flow accepts a a single App Object as input**, it will run on every selected App Object instance individually. That is, it will run the Data Flow repeatedly: once for every app object instance selected. For instance, let's say that the Data Flow in the above example (ostensibly one that sends a follow up email) functions this way. It accepts a single App Object (or a "Feedback Object") as input, and runs twice: first it runs and sends an email to leo@airkit.com, and then it runs again and sends another email to chandra@airkit.com.


**When a Data Flow accepts a List of App Objects as input**, it will run only once, on a List generated from every selected App Object Instance. If we now assume that the above example functions this way, the input given into the Data Flow would look as follows: 




```json Airscript
[  
 {  
  "Email": "leo@airkit.com",   
  "Feedback": "It's okay.",   
  "Notes": "Need to follow up",   
  "Resolved": FALSE  
 },   
 {  
  "Email": "chandra@airkit.com",  
  "Feedback": "It's great!",   
  "Notes": "Need to follow up",   
  "Resolved": FALSE  
 }  
]
```


Data Flows that accept input in this way ought to be used exclusively in cases where the Data Flow requires multiple App Object instances in order to function as intended, such as in cases where properties of App Object instances need to be directly compared. While it is possibly to craft a Data Operation that repeatedly loop through a list of App Object instances and does the same thing to each of them, this introduces an extra layer of complication that ought to be avoided when possible.


# Step 2: Add the Data Flow to the Portal Page


Once you've built out a [Data Flow](https://support.airkit.com/docs/data-flows) that meets the [constraints](#h_01FCP9B4GKYV2YBV4B5Y7MHY7P) given above, save your application and toggle over to the [Portal Builder](https://support.airkit.com/docs/portal-builder-Portal-Builder). (Saving your application ensures Portal Builder will have access to the Data Flow you just created.) [Access your Data Grid](https://support.airkit.com/docs/portal-capabilities#h_01FCPJYGPV6KEWXDCKVGY3S8F7) and click on the "Add Data Flow" button in the Inspector, nested under Data Flow. From there, you can select which Data Flow you want from a dropdown menu of relevant Data Flows (that is, Data Flows that accept input in one of the [required formats](#h_01FCP9B4GKYV2YBV4B5Y7MHY7P)):


![2021-08-09_17-28-26__1_.gif](./assets_v1714/running-data-flows-from-a-data-grid-portal-page-v1714-1).gif)


After selecting a Data Flow to associate with the Data Grid, label the button that will run the Data Flow from the Data Grid. Multiple Data Flows can be added to a single Data Grid, so it's important to give each button a unique name that tells Portal users important information regarding the Data Flow that the button will trigger:


![2021-08-09_17-31-05__1_.gif](./assets_v1714/running-data-flows-from-a-data-grid-portal-page-v1714-2).gif)

# Step 3: Publish and Test


Most components of an app build can be fully emulated by [Previewing](https://support.airkit.com/docs/app-preview) the app, but this is not the case with Portals, because Portals aren't part of an app proper; they're a tool for internal (though non-developer) users as opposed to app users. 


In order to test and confirm that a [Data Flow](https://support.airkit.com/docs/data-flows) built into a Data Grid is running as intended, you'll need to [publish your app](https://support.airkit.com/docs/publishing-your-application) and the access the Portal by then accessing the URL associated with the Portal in [Configuration Builder](https://support.airkit.com/docs/configuration-builder). For more on how to associate URLs with your organization, check out [Connecting your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit), and for more on how to access a published Portal Page, check out [Accessing Portal Pages](https://support.airkit.com/docs/portal-capabilities#h_01FCPJYGPV6KEWXDCKVGY3S8F7).


Upon accessing the Data Grid Portal Page in question, you should see the button associated with Data Flow in the upper right corner. Note that the label on the button matches the label you gave it in the Portal Builder Inspector:

<img src="./assets_v1714/running-data-flows-from-a-data-grid-portal-page-v1714-3.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

When multiple Data Flows are associated with a single Data Grid, the buttons will be arranged as follows:


<img src="./assets_v1714/running-data-flows-from-a-data-grid-portal-page-v1714-4.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

Now you can run your Data Flows on any number of your saved App Objects! Simply select them by clicking on the check box to the left of the relevant object or objects, and then click on the button indicating the Data Flow you want to run:


<img src="./assets_v1714/running-data-flows-from-a-data-grid-portal-page-v1714-5.gif" alt="organizing info" style="max-width: 450px; width:100%;"/>