Datastores are AirData's conceptual way of grouping tables and data. A Datastore contains information about [AirData App Objects](https://support.airkit.com/docs/airdata-app-objects) and all the data or rows stored in the AirData. Datastores are particularly useful for setting up different environments like Production and Staging. 

# Datastore and Profiles


A newly-created organization comes with three default pre-built Datastores -- **Development**, **QA**, and a **Production** Datastore. The pre-built Datastores are then tied to newly created applications which come pre-configured with a **Development**, **QA**, and **Production** profile, and are automatically connected to the corresponding Datastore.  These pre-configured Datastores and profiles enable builders to easily work with separate containers of data that tie to one application. For example, when building out an application and storing a user's contact information in AirData, app builders are able to use the **Development** profile to test writing data back to AirData. Then when ready to test, app builders can change the profile to **QA** and write data to the **QA** Datastore, and lastly when ready for production, the profile can be changed to **Production** to write to the **Production** datastore. 


Profiles contain the configuration information for a published instance of an application. You can modify the profile information in Configuration Builder. The profile is selected at the top of the Configuration Builder. To modify the data source used with a Profile. Select the profile from the dropdown at the top of Configuration Builder.


<img src="./assets_v1714/datastores-v1714-0.png" alt="organizing info" style="max-width: 250px; width:100%"/>


With the desired profile selected, select the Data Store and save. This will bind the Datastore to the profile. When an app is deployed or previewed, it will use the associated Datastore.


![mceclip2.png](./assets_v1714/datastores-v1714-1.png)


# App Objects binding to Data Stores


AirData App Objects are objects created within Data Builder that bundle data fields together. Once defined, AirData App Objects can be used throughout an app wherever [data types](https://support.airkit.com/reference/data-types-overview) are used. When an App Object is defined, the definition is stored in the Datastore.


When an AirData App Object is used to store data, the data is stored in the table. This makes Datastores an ideal place for storing configuration information for each environment.


To demonstrate this, let's create two different sets of towing services for our app. One set will be mock data used in the development environment for testing, and one set will be the data shown to the user. This approach's benefit is that there is no contact to production towing services while testing in development.


When an app is created, it comes pre-configured with a **Development**, **QA**, and **Production** profile that are tied to their corresponding Datastores. Select the **Production** profile from the profile dropdown at the top of the web page. This profile is pre-configured to point to the **Production** Datastore.


Next, go to Data Builder. Create a new AirData App Object by clicking the + icon at the top of the tree. Name the app object "Towing Provider" and give it the properties ```name*``` (Text) and ```phone``` (Phone). Enter two to three records of real towing companies and **Save**. A modal will appear indicating the 'TowingCompanies' App Object will be created in the Production datastore. Click **Continue and Save**. This will serve as the **Production** data. This process is important, as it ensures the changes you make to the app object are reflected. 


![mceclip3.png](./assets_v1714/datastores-v1714-2.png)


Then change the profile to the **Development** Profile and enter two or three records of towing companies to represent test data. Click **Save**. A similar modal will appear to indicate the 'TowingCompanies' App Object will be created in the **Development** Datastore. This will serve as data for testing.


Lastly, Switching between profiles will switch the data available in the Towing Provider database.


![2021-06-09_18-06-51__1_.gif](./assets_v1714/datastores-v1714-3).gif)


# Exporting and Importing Data


Inside Data Builder, it is possible to export and import data into App Objects. This data will be stored with the Datastore. Exporting data from an AirData App Object is as simple as selecting the Object in Data Builder. There is an "Export table as CSV" button in the inspector on the right.


To import data into an AirData, format the data in a spreadsheet app in the columns match each of the AirData App Object fields. Copy the data from the spreadsheet and paste it in a new row on the destination table.


![AirTow-Datastore-paste.gif](./assets_v1714/datastores-v1714-4.gif)


Data can also be shared and imported from an existing app object. To import an app object, in Data Builder, click on the '+' icon next to App Objects and click on **Import Object**. 

<img src="./assets_v1714/datastores-v1714-5.png" alt="organizing info" style="max-width: 350px; width:100%"/>

A modal will pop up with all of the app objects in the Organization that can be imported. One the App Object that is to be imported is identified, click on the **Import** button to import it to the application. Then hit **Save** and refresh the page to see the data appear.