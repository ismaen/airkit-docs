The Data Builder is where you'll create custom [App Objects](https://support.airkit.com/docs/airdata-app-objects) and view data that has been saved to [AirData](doc:airdata). It is also where [Custom Data Types](ref:custom-data-types) are accessed and edited.

Like most Builders, the layout of the Data Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector.


![Data_Builder.png](./assets_v1714/data-builder-v1714-0.png)


# Tree


The Tree is where you'll find an expandable and collapsible breakdown of App Objects and Custom Data Types. The Object or property you select in the Tree determines exactly what is displayed in the Stage and the Inspector.


The structure of the Tree is structured into three levels, which nest as follows:

* Object Type (App Objects, Custom Types, Identity Objects)
  * Object
    * Properties of the object

## App Objects and Identity Objects

App Objects define how data is structured and stored within AirData. They are entirely customizable and can contain any number of properties of any Data Type.

The Identity Object is a special type of App Object that comes pre-defined in every app. It is important because it defines the structure of data pertaining to the [Actor](https://support.airkit.com/docs/actors), the customer going through an Airkit App. The ```actor``` variable is a type of Identity, and it is crucial that the ```actor``` variable have access to way the Identity object is structured. 

In the vast majority of use cases, no data will actually be stored under the Identity object. The presence of the Identity object is important because it structures data that is saved and accessed during the relatively short-term length of a Journey; it is not often used for long-term data storage the way most App Objects are. 

The following example shows a fully expanded Tree in the Data Builder. In this Data Builder, there are two objects: ```Identity``` and ```Survey_data```. ```Survey_data``` has three (```Name```, ```Pet```, and ```Number_of_Pets```), while ```Identity``` has six associated properties (```first_name```, ```last_name```, ```full_name```, ```email```, ```phone```, and ```time_zone```):

<img src="./assets_v1714/data-builder-v1714-1.png" alt="organizing info" style="max-width: 200px; width:100%"/>


### Adding App Objects


New App Objects can be added by clicking the '+' button on the upper right corner of the Tree.

<img src="./assets_v1714/data-builder-v1714-2.png" alt="organizing info" style="max-width: 300px; width:100%"/>

There are three different types of objects you can add: App, [Place](https://support.airkit.com/reference/place-variable-type), or [Schedule](https://support.airkit.com/docs/schedule-objects). Place and Schedule objects are specifically designed to work with Airkit's mapping and scheduling components; they are automatically generated with the relevant properties. App Objects are user-defined objects; they can have any number of properties, which themselves might be any [primitive type](https://support.airkit.com/reference/data-types-overview) or even other App Objects. 


App Objects serve as custom data types that you can use through your app-building process. 


### Importing Objects and Creating Datastores


In addition to allowing the creation of new App Objects, clicking the '+' button on the upper right corner of the Tree provides the option to import objects and create Datastores.


Importing data allows you to directly move data saved on your computer into Airkit Data Builder, as long as the data is formatted in a spreadsheet app such that the columns match each of the AirData App Object fields. For a more detailed dive into how to import and export objects, check out [Exporting and Importing Datastores](https://support.airkit.com/docs/datastores).


Datastores are AirData's conceptual way of grouping tables and data. A datastore contains information about all the data stored in the AirData, and they are particularly useful for setting up different environments like Production and Staging. For more on how to work with Datastores, check out [Datastores](https://support.airkit.com/docs/datastores).


## Custom Data Types

Custom Data Types are objects. Each application can have access to arbitrarily many Custom Data Types, Each Custom Data Type consists of any number of properties, structured into key-value pairs. A property can expect any primitive Data Type as well as other Custom Data Types.

In concept and in practice, Custom Data Types are similar to AirData App Objects. In the context of Data Builder, they are created and edited in the same way. The fundamental difference is that AirData App Objects define a way to structure data that can be saved to AirData, whereas Custom Types can only be used to define local variables for reference within the context of a Journey.

The following example shows how two separate Custom Data Types appear in the Tree of the Data Builder. The first Custom Data Type (**Example Custom Type**) has two properties (```text``` and ```number```). The second Custom Data Type (**Auto-Generated Type**) has seven properties (```activity```, ```type```, ```participants```, ```price```, ```link```, ```key```, and ```accessibility```). 

<img src="./assets_v1714/data-builder-v1714-3.png" alt="organizing info" style="max-width: 200px; width:100%"/>

Note the similarities to how App Objects are organized. 

# Stage

## App Objects and Identity Objects

When viewing an App Object or an App Object property, the Stage displays the data that has been saved to the App Object. 


Gathered data is displayed in a table. The interface is reminiscent of a spreadsheet, with each row representing an individual instance of an App Object and each column corresponding with a particular property. Every App Object has its own table.


The following example shows how the Stage appears when examining an Object with three properties: ```Name``` (a [string](https://support.airkit.com/reference/the-text-variable-data-type)), ```Pet``` (another string) and ```Number_of_Pets``` (a [Number](https://support.airkit.com/reference/the-number-variable-data-type)). There are three instances of this object stored. Note that, on the left of each instance, there's a trash symbol; clicking on it will delete the instance and all associated data: 


![Screen_Shot_2021-06-21_at_4.05.53_PM.png](./assets_v1714/data-builder-v1714-4.png)


Visualizing your saved data in this way allows you to quickly skim through it and notice obvious trends. It also makes it easy to confirm data is being saved as intended. 


### Filters


To further simplify the process of examining data, Airkit makes it possible to filter data based on specified criteria directly in the Stage. To the right of each object property is a filter icon; clicking it brings up filtering options.


![2021-06-21_16-14-52__1_.gif](./assets_v1714/data-builder-v1714-5).gif)


These filter options can ensure that a specific filed has a particular value, meets a certain threshold, or is equal to a specific value. Filtering out data unrelated to your current search cuts down on noise and makes it even easier to notice trends within the clusters of data you care about. These filter options are analogous to the filter options available in Portal Builder. 

## Custom Data Types

When viewing a Custom Data Type, the Stage displays an example how the Custom Data Type might appear in [Airscript Quick Start](doc:airscript-quick-start). Note that the values associated with each property do not represent any real data, only dummy data:

<img src="./assets_v1714/data-builder-v1714-6.png" alt="organizing info" style="max-width: 400px; width:100%"/>

# Inspector


The Inspector is where you can examine and modify individual elements within the Data Builder. The exact functionality available within the Inspector varies depending on what is being Inspected.

Unlike the Inspectors associated with most Builders, the Data Builder Inspector does not make changes that will be reflected in the Stage; most changes made in the Data Builder Inspector only define changes to how data will be displayed elsewhere. 


## Display Expression (Object Level)


Displays is a drop-down menu that allows you to choose which property of the object will be displayed in a cell should this object be used as a property in a separate object.


## Property 


Provides means to examine and edit fundamental characteristics of a property, including other names its gone by (recorded as"Field Aliases") and the [data type](https://support.airkit.com/reference/data-types-overview) of the property. This is also where you can set restrictions on acceptable values for that property.


## Formatter/Parser (Property Level)


Modify the way that data is viewed and stored in [external Portals](https://support.airkit.com/docs/portal-builder).


* **Formatter** - Changes how the data will be viewed in Portals.
* **Parser** - Changes how the data will be stored in Portals.


You can utilize Airscript to alter the format of the displayed data. To reference the data, use the namespace **@**. The **@** symbol corresponds to the field data.


The following example shows how Airscript functions can be entered as input for either Formatter or Parser. The function [FORMAT_PHONE](https://support.airkit.com/reference/format_phone) takes the data in every cell in the relevant column (which represents, ostensibly, phone numbers) and converts it into the international phone number format. If this function is entered into the Formatter, it will only change the way these phone numbers will be displayed in Portals; If this function is entered into the Parser, it will change the way the phone numbers are stored:



```javascript Airscript
FORMAT_PHONE(@, "INTERNATIONAL")
```

## Validation


Places rules on how data will be displayed in [external Portals](https://support.airkit.com/docs/portal-builder). No changes made here will impact the way data is displayed in the Data Builder Stage; they will only be noticeable when viewing Portals.


There are three validation rules that you can add to an app object field. (One other, *Is Unique*, appears when you click the '+' icon to the right of the **Validation** section in the Inspector, but this is deprecated; its functionality has been moved under **Constraints**.)

<img src="https://a01-support.airkit.com/data-builder/2021-06-24_11-04-35%20(1).gif" alt="organizing info" style="max-width: 350px; width:100%"/>


* **Is Required** - ensures that this field must have data if its being entered by a user. The field could still have empty data inside Object-Service. This coupled with the constraint **Not Null** ensures that data always is present.


* **Length is Within Range** - allows you to set an upper and lower bound on the length of the data. This will perform the Airscript function [LENGTH](https://support.airkit.com/docs/airdata-app-objects) on your input.


* **Custom Rule** - utilizes Airscript to allow you to create more complex validation rules. The custom expression is expected to result in a [Boolean](https://support.airkit.com/reference/the-boolean-variable-data-type). Instances where your custom Airscript output TRUE will be marked as valid; instances where your custom Airscript output FALSE will be marked as invalid. The @ symbol should be used as a placeholder for the value the relevant object property. For instance, the following example shows how to use the function [ISPHONE](https://support.airkit.com/reference/isphone) to validate that each instance of data is a [valid phone number](https://support.airkit.com/reference/the-phone-variable-data-type):



```javascript Airscript
ISPHONE(@)
```

## Constraints


Constraints place limits on what data can be added when attempts are made to add data; App Objects that do not meet the constraints will not be saved.


There are four unique Constraints that you can add to an app object field. 

<img src="./assets_v1714/data-builder-v1714-7.gif" alt="organizing info" style="max-width: 350px; width:100%"/>


**Unique** - ensures that no two instances have the same value for this field. This signifies that this column can be used as a primary key: a way to identify a single row of data.


**Not Null** - ensures that this field must have a value and that value cannot be **NULL**. This constraint is helpful in requiring input if you decide to create a [Data Grid Portal page](https://support.airkit.com/docs/portal-builder).


**Default Value** - provides a default value to this field. If no data is entered by the user, this default value will be recorded into AirData.


**User Variable** - acts as a row-level permissioning for the data.


Be careful: constraints will be applied to retroactively all data saved in the relevant App Object, and all instances where the constraints are not met will be permanently deleted as soon as the constraints are applied. 


# Storing and accessing your data in Airkit


Most commonly, data is gathered as users go through their [Journeys](https://support.airkit.com/docs/journeys); connecting information entered by users is done by creating [Data Flows](https://support.airkit.com/docs/data-flows) – specifically, ones that include [AirData Queries](https://support.airkit.com/docs/airdata-querying-capabilities) – in the Connection Builder. Data can also be added manually or while testing AirData Queries in the Connection Builder directly.


Once you’ve saved data, you can click on one of your objects in the Tree to see all the data associated with that object. You can select on any given cell to modify data, and you can scroll to the last row to add new data to this.


You can also create [Data Flows](https://support.airkit.com/docs/data-flows) to access and analyze your data directly within your apps: [AirData Queries](https://support.airkit.com/docs/airdata-querying-capabilities) can perform CRUD operations.


If you want to access your data outside of the Airkit Studio, your tables can easily be exported into CSV format. You can also use Portal Builder to create external portal pages that provide access select information from your Airkit app without giving them to access anything else.