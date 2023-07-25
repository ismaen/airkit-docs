The Connection Builder is designed to be your gateway to the outside world, as well as the place where you can design complex data interactions. It's the Builder that makes it easy to use and modify data, both internal and external.


Like most Builders, the layout of the Connection Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which might be the Inspector. Note that the Inspector will not always be visible; depending on what's being displayed in the Stage, there might not be a need to access the Inspector. For instance, when examining a Data Flows, the Inspector will be present to show the variables that are available within the Data Flow:


![2021-11-03_14-21-12.png](./assets_v1714/connection-builder-v1714-0.png)


On the other hand, when examining a Web Links, all relevant information is displayed in the Stage, and so there is no need to access the Inspector:


![2021-11-03_14-24-05.png](./assets_v1714/connection-builder-v1714-1.png)


# Structure

## Tree


The Tree is where you'll find an expandable and collapsible breakdown of the connections you have built out as part of your app. Airkit automatically splits these connections up into five types: **Data Flows**, **Web Links**, **Subscriptions**, **Periodic Tasks**, and **User Defined Functions**. If you want to create a new connection, click the '+' sign to the right of the type of connection you want to add. If you want to delete a connection after it's been created, click on the trash icon to the immediate right of the undesired connection.

<img src="./assets_v1714/connection-builder-v1714-2.gif" alt="organizing info" style="max-width: 350px; width:100%"/>


## Stage


The Stage displays a visual representation of the connection you are accessing. Exactly what is displayed in the Stage varies depending on the type of connection you are building or editing.


## Inspector


The Inspector is where you can examine and modify details associated with Data Flows and Periodic Tasks. The Inspector will not appear when examining Web Links or Subscriptions, as all relevant information is displayed in the Stage.


# Connection Types


## Data Flows


[Data Flows](https://support.airkit.com/docs/data-flows) are custom connections. Conceptually, Data Flows work like functions: they take in input, process it, and return the resulting output. Once a Data Flow has been built, it can be initiated as a [Periodic Task](https://support.airkit.com/docs/setting-up-periodic-tasks) (see below) or as an [Action](https://support.airkit.com/docs/action-builder) within your application.


Data Flows are made up of component parts called [Data Operations](https://support.airkit.com/reference/data-operation-overview), which define how input is processed. Processing input might entail anything from [making HTTP requests](https://support.airkit.com/reference/http-request-data-operation) to [sending emails](https://support.airkit.com/reference/the-send-email-data-operation) to [running another Data Flow](https://support.airkit.com/reference/the-run-data-flow-data-operation). A single Data Flow might consist of any number of interconnected Data Operations, though these Data Operations do not appear nested underneath them in the Tree; building Data Flows out of Data Operations is done in the Stage.


### Stage


When working with Data Flows, the Stage is where you'll see and build out the individual connections within. Upon creating a new, custom Data Flow, the Stage appears as follows. The top box, **Start**, keeps track of the input the Data Flow requires and the bottom box, **End**, is where you'll declare which of the internal variables the Data Flow will return. Note that, as this newly-created Data Flow is blank, no input is defined, and there are no return values to choose from. Also note that there is no way to add input values within the Stage; keeping track of the variables a Data Flow has access to – including the direct input – is the domain of the Inspector:

<img src="./assets_v1714/connection-builder-v1714-3.png" alt="organizing info" style="max-width: 250px; width:100%"/>


The individual Data Operations that the Data Flow consists of go between the *Start* box and the *End* box. You can add a new Data Operation between connections by clicking on the '+' icon between them directly in the middle of the stage. Individual Data Operations can be deleted by clicking on the trash icon to their immediate right:

<img src="./assets_v1714/connection-builder-v1714-4.gif" alt="organizing info" style="max-width: 450px; width:100%"/>

Once a Data Operation has been added, its details can be edited directly within the Stage. There are many different types of Data Operations, and how each one appears and can be edited will differ according to functionality. For a closer look into the different types of Data Operations, check out the [reference documentation](https://support.airkit.com/reference/data-operation-overview).


In the process of creating and editing Data Operations within a Data Flow, it is a good idea to test how they run to ensure they work as intended. This can be done by clicking on the 'Run' button within a Data Operation. Often, however, a Data Operation requires access to other variables – most commonly, direct input – in order to run. To streamline the process of testing, dummy input can be defined directly in the Stage. Once the required input has been defined in the Inspector, example input of the correct [data type](https://support.airkit.com/reference/data-types-overview) is automatically generated. This dummy input can be both examined and edited in the **Start** box, and when individual Data Operations are run, they will use the dummy values in place of the input variables:

<img src="./assets_v1714/connection-builder-v1714-5.gif" alt="organizing info" style="max-width: 300px; width:100%"/>



When Data Operations are built out, relevant variables will be auto-generated to account for their output, which can be used as input in downstream Data Operations. The more complex a Data Flow, the more of these variables will be generated, making it important to designate precisely which one is the desired output of the Data Flow as a whole. Once a Data Flow has been fully built out, you can specify which internal variable it will return by selecting the desired output from a dropdown menu in the **End** box.

<img src="./assets_v1714/connection-builder-v1714-6.gif" alt="organizing info" style="max-width: 300px; width:100%"/>

For more on how internal variables are generated and how dummy values are stored for the sake of testing, see the Inspector section.


### Inspector


When examining Data Flows, the Inspector displays the relevant internal variables. These are separated into two expandable and collapsible sections: **Start**, and **Variables**. 


#### Start


The **Start** section in the Inspector is where you can define input that the Data Flow requires. This is done by clicking on the '+' icon to the right of 'Inputs' and selecting the desired [data type](https://support.airkit.com/reference/data-types-overview) of the additional input. Upon creation, you will be directed to name the input variable, after which a dummy value of the correct data type will be attributed to the variable for testing purposes. This dummy value will not be accessible outside of the Connection Builder; it will certainly not influence the behavior of the Data Flow when used as part of your app. It will only be used when a value for that variable is required in order to test Data Operations within the Web Flow within the Stage.


The following example shows how to add a number input, named ```input_number```, to a Data Flow. Note that ```input_number``` is automatically set to the value '1' for testing purposes. This is not because the number one has any particular significance in the context of this Data Flow; it is only because 1 is an arbitrary [Number](https://support.airkit.com/reference/the-number-variable-data-type), and thus makes a passible dummy variable. 

<img src="./assets_v1714/connection-builder-v1714-7.gif" alt="organizing info" style="max-width: 250px; width:100%"/>

Upon their creation, dummy variables can be changed in the Stage, in the **Start** box. 

#### Variables


The **Variables** section keeps track of all internal variables that are not required as input. (Remember: Data Flows might consist of any number of Data Operations, and Data Operations often produce their own output, which can be used as input for Data Operations downstream.) All variables automatically generated by Data Operations are found under **Variables**.


The following example shows what appears in the Inspector after a [Transform Data Operation](https://support.airkit.com/reference/the-transform-data-operation) has been added has been added but before it has been run. Note that the automatically-generated variable, called ```transform```, is present but undefined:

<img src="./assets_v1714/connection-builder-v1714-8.png" alt="organizing info" style="max-width: 300px; width:100%"/>


Once the Transform Data Operation has been defined – in this example, so that it outputs the sine of ```input_number``` – and run, the value of ```transform``` will change to reflect that:

<img src="./assets_v1714/connection-builder-v1714-9.png" alt="organizing info" style="max-width: 300px; width:100%"/>

When downstream Data Operations call upon the ```transform`` variable, they will, when run for testing purposes, use the value 0.8414709848078965 – at least until that value changes as a result of the Transform Data Operation being modified and run again to yield a different result.


## Web Links


The *Web Links* section allow you to define Web Links and [App APIs](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions) that can be incorporated into your application. These can be made into [Events](https://support.airkit.com/docs/events), including [Starting Events](#h_01F9FDQ03BKRA48ZM1N86EJP0J), which trigger the start of a [Journey](https://support.airkit.com/docs/events).


### Stage


When working with Web Links and [App APIs](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions), the Stage can be used to view and modify what the link or the API call fundamentally is. You can define the URL associated with a link, designate the exact HTTP request that will be sent to an API, and access the details of Journey Mapping.


## Subscriptions


[Subscriptions](https://support.airkit.com/docs/passing-data-from-external-systems) are a mechanism by which Airkit apps can receive (and subsequently respond to) to data updates from external sources. These can be made into [Events](https://support.airkit.com/docs/events) that influence app behavior.


### Stage


When working with Subscriptions, the Stage can be used to view and modify the data source and the category of webhook. It can also be used to access the details of Journey Mapping.


## Periodic Tasks


[Periodic Tasks](https://support.airkit.com/docs/setting-up-periodic-tasks) schedule [Data Flows](https://support.airkit.com/docs/data-flows) to run at specific times. 


### Stage


When working with a Periodic Task, the Stage displays a log of all instances where the Periodic task has been run.


### Inspector


When examining a Periodic Task, the Inspector is where you can can view and modify the Data Flow being run periodically. You can select when Data Flow to run as well as when to run it.


## User Defined Functions


[User Defined Functions](https://support.airkit.com/docs/user-defined-functions) are custom functions made out of and parsable by [Airscript](https://support.airkit.com/docs/airscript-quick-start). They can be used as part of an application in the same way as out-of-the-box Airscript functions can.


### Stage


When working with User Defined Functions, the Stage displays the **Function Body**, which dictates the behavior of the User Defined Function in terms of Airscript and the designated input. 


### Inspector


When inspecting a User Defined Function, you'll find the means to edit the details of the function name as well as the input it expects and the output it will return.