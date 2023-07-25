AirData is Airkit’s internal system of record. It makes it easy to structure, save, and query data gathered from your Airkit apps. This data is organized in the form of custom [App Objects](https://support.airkit.com/docs/airdata-app-objects).


![Screen_Shot_2021-06-21_at_4.05.53_PM.png](./assets_v1714/airdata-v1714-0.png)


# Displaying your data


It's possible to view data saved within AirData in two locations:


* Data Builder - view your data directly within Airkit
  * Right out of the box, the Data Builder provides a means to view everything saved in AirData.
* Data Grid Portal Page - view data in an external Portal
  * Portals need to be built out in the Portal Builder before they can be used to access data. They are highly customizable, giving you fine control of exactly what and how data is displayed. Most commonly, Portals are designed for internal use, as they allow non-developer teams to view and even work with important data while preventing them from making any changes to the app itself by accident.


In both locations, your data is displayed in a table. The interface is reminiscent of a spreadsheet or SQL database, with each row representing an individual instance of an App Object and each column corresponding with a particular property. Every custom App Object has its own table.


For more on accessing your data in a particular location, check out the links above.


# Querying Capabilities


[AirData Queries](https://support.airkit.com/docs/airdata-querying-capabilities) can perform basic CRUD operations on your AirData. Typically, this is done by creating Data Flows – specifically, ones that include [AirData Request Data Operation](https://support.airkit.com/reference/airdata-request-data-operation) – in the Connection Builder. The AirData Request Data Operation can also be run in the Connection Builder directly, either to test that a Query runs as intended or to perform a one-off interaction with your data.


# Encrypting Data


App Object fields can be individually [encrypted in AirData](https://support.airkit.com/docs/encrypting-data) using the **Encrypt** flag when the field is selected in Data Builder. When encrypting data within AirData, there is the capability of bringing your own encryption key or using [encryption keys](https://aws.amazon.com/kms/) provisioned with the Airkit [Organization](https://support.airkit.com/docs/airkit-organizations). When an Organization is provisioned, three encryption keys get created by default and are associated with the three Datastores (**Development**, **QA**, and **Production**). 


There are some limitations to keep in mind when encrypting fields, which include not being able to search or filter on fields that are encrypted.