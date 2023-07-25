Portals are dashboards that make it possible to view and edit data stored in [Airdata](https://support.airkit.com/docs/airdata) without accessing anything under the hood. Most Portals are built out for use by teammates that have been assigned the [role](https://support.airkit.com/docs/managing-user-roles) of Agent, which does not grant them permission to work within [Airkit Studio](https://support.airkit.com/docs/studio) proper. A single Airkit app can be associated with only a single Portal, but that Portal can consist of arbitrarily many Portal Pages. Portals and Portal Pages can be created in the [Portal Builder](https://support.airkit.com/docs/portal-builder).




### Accessing Portal Pages


Most components of an app build can be fully emulated by [Previewing](https://support.airkit.com/docs/app-preview) the app, but this is not the case with Portals, because Portals aren't part of an app proper; they're a tool for internal (though non-developer) users to view app-related data. Portals are not part of a user's [Journey](https://support.airkit.com/docs/journeys). 


In order to test and confirm that a Portal is functioning as intended, the app needs to be [published](https://support.airkit.com/docs/publishing-your-application), at which point the Portal can be accessed by going to the URL associated with the Portal in [Configuration Builder](https://support.airkit.com/docs/configuration-builder). For more on how to associate URLs with your organization, check out [Connecting your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit).


Multiple Portals can be associated with a single URL. When this is the case, you can select the Portal you want to view by clicking on the icon in the upper left corner and selecting the desired Portal. The follow example shows what it looks like to toggle between two available Portals: *Hello, Portals!* and *Portal Experiments*.


![2021-08-09_17-50-44__1_.gif](./assets_v1714/portal-capabilities-v1714-0).gif)


Portal Pages are displayed on the upper right of a Portal. To open the desired Portal Page, click on the one you want to view. The following example shows what it looks like to toggle between two available Portal Pages: *Feedback Object* and *List Test*: 


![2021-08-09_17-53-37__1_.gif](./assets_v1714/portal-capabilities-v1714-1).gif)


#### Additional Security


Permissions are usually dictated by the [role of the user](https://support.airkit.com/docs/managing-user-roles-Managing-User-Roles), but Portal Pages provide the option of additional security. Users, upon [being invited](https://support.airkit.com/docs/adding-users-to-airkit) or managed in the [Console](https://support.airkit.com/docs/console), can be assigned User Variables with associated values. Access to Portal Pages can then be limited only to users with User Variable/value pairs that match the User Variable/value pairs associated with the Portal Page, as specified in the *Permissions* section in the Inspector of the [Portal Builder](https://support.airkit.com/docs/portal-builder).


For instance, say you want to create a Portal Page that is only relevant to your Sales Team. You can assign every user on your Sales Team a User Variable called `Team` and give it the value "Sales." Then when finalizing the Portal Page, you can define the User Variable `Team` and also give it the value "Sales," so that only users with the matching User Variable/value pair – that is, users on your Sales Team – will be able to access the Portal Page.


When a user accesses a Portal containing a Portal Page they do not have access to, it will appear as though the restricted Portal Page does not exist at all.


### What can you do with a Data Grid Portal Page?


One of the commonly used types of Portal Page is the [Data Grid](https://support.airkit.com/docs/portal-data-grids), which allows anyone accessing the Portal to interact with data stored in [AirData](https://support.airkit.com/docs/airdata). Each Data Grid is associated with an [App Object](https://support.airkit.com/docs/airdata-app-objects). By default, a Data Grid displays the data that has been saved to the App Object in exactly the same way that the [Stage](https://support.airkit.com/docs/data-builder) displays the same information within the [Data Builder](https://support.airkit.com/docs/data-builder). However, a key difference is that it's possible to change or limit exactly which properties of an App Object are displayed; this can be used to make the Data Grid more intuitive to non-developers and to limit the visible information to only that which is relevant to the people who will be regularly accessing the Portal Page. See documentation on the [Portal Builder](https://support.airkit.com/docs/portal-builder) and [Data Builder](https://support.airkit.com/docs/data-builder) for more information on how to customize how data is displayed within a Data Grid.


In addition to allowing Agents to view information stored in [AirData](https://support.airkit.com/docs/airdata), Data Grids also make it easy for Agents to interact with data in various pre-approved ways. For instance, it is possible to download the displayed data as well as [upload a CSV file that appends additional data to it](https://support.airkit.com/docs/uploading-a-csv-to-import-data). The [Portal Builder](https://support.airkit.com/docs/portal-builder) also provides fine control over which object properties Portal viewers will have the capacity to edit and whether or not Portal viewers will be allowed to delete whole rows of data. One of the most powerful ways Portal viewers can interact with data in a Data Grid is by running [Data Flows](https://support.airkit.com/docs/data-flows) on select App Object instances.


By [associating relevant Data Flows to a Data Grid](https://support.airkit.com/docs/running-data-flows-from-a-data-grid-portal-page), it's possible to streamline the most common data tasks. There are many possibilities for automation. A simple example involves a Data Grid that displays an App Object containing survey data with a column for email address. A Data Flow can be built that automatically sends follow-up emails to email addresses selected by the Portal viewer. Note that it can perform this Data Flow on any number of App Object instances at at time:


<img src="./assets_v1714/portal-capabilities-v1714-2.gif" alt="organizing info" style="max-width: 450px; width:100%;"/>