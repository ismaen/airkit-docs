Airkit allows you to collect, use, modify, and remit data. 

What is Data?
-------------


Data is information that can be stored or used in your application. Data in Airkit has many different [data types](https://support.airkit.com/reference/data-types-overview). Data can be simple types like [Text](https://support.airkit.com/reference/the-text-variable-data-type) or [Number](https://support.airkit.com/reference/the-number-variable-data-type), complex types like [Currency](https://support.airkit.com/reference/the-currency-variable-data-type) or [Datetime](https://support.airkit.com/reference/the-datetime-variable-data-type), or objects with a customized structure, such as [AirData App Objects](doc:airdata-app-objects) or [Custom Data Types](ref:custom-data-types).

Data can be collected from a user or stored in App and used as a configuration.


3 Ways To Store & Access Data
-----------------------------


### 1) Variable & Journey State


Variables are one way to store and access Data. Variables can be defined at different scopes to have different availability throughout an application. The data held in a variable reference can be changed throughout the lifetime of the app based upon events and actions. 


#### Defining Variables in Namespaces and Scopes


Namespaces refer to regions where we can store data. Scopes are how we access variables in each of the regions. For a detailed understanding, please check out this document on [variable scopes](https://support.airkit.com/docs/variable-scopes). There are several different variable scopes for working with data. Some of them include:


**Session -** accessible anywhere throughout the app builder and journey builder. They are tied to a specific user's journey.



```javascript Airscript
session.first_name
```

Defining variables at the session level happens in [Journey Builder](https://support.airkit.com/docs/journey-builder). Click on the canvas and the inspector will show available session scoped events.


![sessionVariablegif.gif](https://a01-support.airkit.com/working-with-data/sessionVariablegif.gif)


**ActivityGroup -**accessible to any web page, action, or event within a specific [Web Flow](https://support.airkit.com/docs/web-flows).



```javascript Airscript
activityGroup.first_name
```

To create a variable on a *Web Flow*, go to [App Builder](https://support.airkit.com/docs/web-builder) and select a *Web Flow* in the *Tree*. In the *Inspector* under the *Variables* section, there is a list of available *ActivityGroup* scoped variables and a button to add new variables.


**Activity -** accessible to any event or control on a given web page.



```javascript Airscript
activity.first_name
```

To create a variable on a *Web Page*, go to [App Builder](https://support.airkit.com/docs/web-builder) and select the *Web Page* from the *Tree*. In the *Inspector* under the *Variables* section, there is a list of available *Activity* scoped variables and a button to add new variables.


When referring to a variable without a scope in a *Web Flow,* the runtime will attempt to find the variable in the most specific level and work up the chain, checking in **activity**, then **activityGroup**, then in **session**. It is possible to have variables named the same name in multiple scopes so it best to be specific when referring to your variables.


#### Accessing the Data


Defined data can be used in expression editors throughout the experience. In this case, the **activityGroup** variable **activity_group_name** is used to set the text for a label.


![ExpressionEditorText.png](https://a01-support.airkit.com/working-with-data/ExpressionEditorText.png)


Updating values in variables can be done through [Set Variable Action](https://support.airkit.com/reference/the-set-variable-action) on an action or event. This action can happen when a user takes an action, such as entering data into a form, clicking on a button, or responding to a text or voice prompt. Because this action uses an expression editor, Airscript can be used with properly scoped variables in updating variable values.


### 2) Storing and Looking Up Records with AirData


AirData is a datastore tied to an app's profile where records can be stored for collection or retrieval. Use [Data Flows](https://support.airkit.com/docs/data-flows) to look up and store your records into [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects). Airkit Studio has a bunch of ways to work with data stored in AirData.


#### Seeing AirData in Data Builder


The data stored in AirData can be viewed in the [Data Builder](https://support.airkit.com/docs/data-builder). Selecting an object in the *Tree* will show you the data already in the AirData Table.


![AirDataTable.png](https://a01-support.airkit.com/working-with-data/AirDataTable.png)


Clicking into a table cell will allow modification of data. Once a row has modified data, it will highlight in a light yellow. Changes will be committed on the next save. Add new rows by clicking on the cell to the right of the *New*text. New rows are highlighted in light green. Just like modified rows, changes will be committed on the next save. Clicking the trash can at the left of a row will mark the row for deletion on the next save.


#### Retrieving Data with Data Flows


Data from AirData can be accessed through [Data Flows](https://support.airkit.com/docs/data-flows) in [Connection Builder](https://support.airkit.com/docs/connection-builder). To retrieve data from the above table, create a new Data Flow in Connection Builder. Select [AirData Request Data Operation](https://support.airkit.com/reference/airdata-request-data-operation) from the dropdown for the first [Data Operation](https://support.airkit.com/reference/data-operation-overview). The above AirData App Object is named **Teacher**, so select that from the dropdown.


![AirDataRunResults.png](https://a01-support.airkit.com/working-with-data/AirDataRunResults.png)


Clicking Play on the Data Operation will return the query results from the AirData table. In the picture above, there were 5 teachers in the **Teachers** AirData table. Returning the entire response is possible at this point, but it is also possible to filter out the results by creating another Data Operation of type [Transform](https://support.airkit.com/reference/the-transform-data-operation). Writing something simple like:



```javascript Airscript
objectService.results
```

will return only the resulting array. Returning the result of the transform will return a [List](https://support.airkit.com/reference/the-list-data-type) of **Teacher** Objects. In addition, additional filtering of the list can be done in the Transform using Airscript's [Query Expression Syntax](https://support.airkit.com/docs/filtering-data-using-query-expression) to pull out all teachers who have been teaching for at least five years.



```javascript Airscript
FROM teacher  
IN objectService.results  
WHERE teacher.years_teaching > 5  
SELECT teacher
```

The result of this transform would be all of the teachers who have a value of **years_teaching** greater than five.


#### Using Datastores


AirData is stored in [Datastores](https://support.airkit.com/docs/datastores). Datastores are collections of AirData that are kept in a specific environment. Different [Profiles](https://support.airkit.com/docs/using-profiles-for-deployment-settings-and-configurations) can use different *Datastores*. Each datastore will have its own version of AirData. Create a clone of a *Datastore,* which is useful when setting up environments for testing. When an app is created, a *Datastore* is created with it. Switching the *Datastore* can be done in [Configuration Builder](https://support.airkit.com/docs/configuration-builder).


### 3) External Systems of Record


External system data can be retrieved, modified, and updated through [Connection Builder](https://support.airkit.com/docs/connection-builder). This data can be used throughout your App. Our [Data Flows](https://support.airkit.com/docs/data-flows) can be used to fetch data from any HTTP API. Once data is ingested into the App through the connection it can be treated like any other [Variable Data Type](https://support.airkit.com/reference/data-types-overview). For detailed instructions on how to get external data, check out [this article](https://support.airkit.com/docs/connecting-to-external-systems).


Using & Transforming Data
-------------------------


There are two main categories of data in the Studio. Data that needs to be gathered from a user and data that needs to be displayed. Gathering data is about creating [Forms and Agreements](https://support.airkit.com/docs/working-with-forms-and-agreements). When we create a [Text Input](https://support.airkit.com/reference/text-input-web-control) on a *Web Page,*Airkit automatically creates a data binding to a text variable on the page. This variable can be displayed on the existing paged, passed to an action like a Data Connection, or an Event. The data can also be passed to future Web Pages in the journey:


![GoodMorning1.png](https://a01-support.airkit.com/working-with-data/GoodMorning1.png)![GoodMorning2.png](https://a01-support.airkit.com/working-with-data/GoodMorning2.png)


In this example, the text is retrieved from the user and passed to the subsequent Web Page to be displayed.


In Addition to viewing, Data can be sent to [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects) or external systems through [Data Flows](https://support.airkit.com/docs/data-flows).


Data might need to be transformed, actually as it was in the example above. In order to create the Text for the Text Label with the name, the Expression editor for the greeting text contained:



```javascript Airscript
"Good Morning, {{first_name}}"
```

This is an example of using an escape sequence in the string for the Label to Insert some AirData. There are more examples in [Working With Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript).


More complicated transformations of data are better done in [Data Flows](https://support.airkit.com/docs/data-flows) in [Connection Builder](https://support.airkit.com/docs/connection-builder) using the [Transform Data Operation](https://support.airkit.com/reference/the-transform-data-operation). This operation can be used for many different things, check out the documentation for more information.


Where to go from here
---------------------


This is just a basic introduction to working with Data within your app. For additional resources please check out the following pages:


* [Data Flows](https://support.airkit.com/docs/data-flows) - How to work with data coming in and going out of your application.
* [Variable Scopes](https://support.airkit.com/docs/variable-scopes) - find out more detailed info on variable scoping.
* [AirData](https://support.airkit.com/docs/airdata) - how is data stored.
* [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects) - Defining custom objects.
* [Forms and Agreements](https://support.airkit.com/docs/working-with-forms-and-agreements) - How to collect data from a user.