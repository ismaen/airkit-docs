Data Grids are a type of [Portal Page](https://support.airkit.com/docs/portal-capabilities) that display individual [App Objects](https://support.airkit.com/docs/airdata-app-objects) similarly to how they are displayed in [AirData](https://support.airkit.com/docs/airdata). (For a discussion on how to access a Data Grid after it's been created in [Portal Builder](https://support.airkit.com/docs/portal-builder), see [Accessing Portal Pages](https://support.airkit.com/docs/portal-capabilities#h_01FCPJYGPV6KEWXDCKVGY3S8F7).) Here, we'll go over the basic structure of a Data Grid Portal Page, as well as the placement and functionality of some important buttons located at the top and leftmost side of the interface.


![2021-08-19_09-13-23.png](./assets_v1714/portal-data-grids-v1714-0.png)


### Portal Navigation


#### Portals Menu


Click the Portals Menu button to select a Portal to open. The Portals available for selection are linked to the [role](https://support.airkit.com/docs/managing-user-roles) and organization signed into.


#### Viewer Profile


Click on the Viewer Profile Button to view information associated with the account being used to access Portals, including the [role](https://support.airkit.com/docs/managing-user-roles) and associated email address. This button also provides the option to log out of said account.


#### Portal Page Tabs


The Portal Page Tabs allow you to toggle between different Portal Pages that are stored under the same Portal. See intro to [this article](https://support.airkit.com/docs/portal-capabilities) for a deeper discussion on the difference between Portals and Portal Pages.


### Data Grid


A Data Grid displays the data associated with an [App Object](https://support.airkit.com/docs/airdata-app-objects); it's similar to how the data is displayed in [AirData](https://support.airkit.com/docs/airdata). The Data Grid itself is reminiscent of a spreadsheet, making it familiar to work with. Like a spreadsheet, each row represents an instance of an App Object and each column corresponds with a property.


Data Grids also make it possible to select individual instances of App Objects by clicking the check box to their left. Selecting one or more of these boxes make it possible to take actions on the designated App Object instances, such as in the following example, wherein two App Object instances are deleted. Note that the Delete button appears only when a box is checked:


![2021-08-19_13-57-39__1_.gif](./assets_v1714/portal-data-grids-v1714-1).gif)


Note also that the Run Data Flows buttons changed color when an App Object instance was selected. Why this occurs is touched on [below](#h_01FDG35NVR90DRADM1DD4K46WX).


### Other Buttons


#### Filter


Click on the Filter button to filter displayed data by specific criteria. Data filtered changes how data is presented in a Data Grid, and what is done by a filter can be easily undone by removing it.


#### Sort


Click on the Sort button to reorganize rows of data based on the alphanumeric value of specified [App Object](https://support.airkit.com/docs/airdata-app-objects) properties. 


#### Run Data Flows


These buttons, which run [Data Flows](https://support.airkit.com/docs/data-flows) on selected rows of data, will only be present if they have been created in the [Portal Builder](https://support.airkit.com/docs/portal-builder). For more on how to add Data Flows to Data Grid, check out [Running Data Flows from a Data Grid Portal Page](https://support.airkit.com/docs/running-data-flows-from-a-data-grid-portal-page).


#### Upload Data


Click on the Upload Data button to append data to the displayed [App Object](https://support.airkit.com/docs/airdata-app-objects) by uploading an appropriately-formatted CSV file. For more on how to do so, check out [Uploading a CSV to Import Data](https://support.airkit.com/docs/uploading-a-csv-to-import-data). 


#### Export Data


Click on the Export Data button to download information displayed in the Data Grid in a CSV file.


#### Column Display


Click on the Column Display button to modify what columns are displayed in the Data Grid. Unchecking a column name will not delete any data; it will only render the column temporarily invisible in the Data Grid. Checking an unchecked column name will render it visible again.