The Portal Builder provides a way to design, create, and edit custom [Portals](https://support.airkit.com/docs/portal-capabilities). Portals are interfaces that allow someone to access select information from your Airkit app without giving them to access anything under the hood. In addition to giving you control over what data is displayed in these Portals, the Portal Builder also makes it easy to streamline actions users of a Portal might want to take with the data, such as sending emails to addresses collected by the app.


Like most Builders, the layout of the Portal Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector: 


![Portal_Builder.png](./assets_v1714/portal-builder-v1714-0.png)


In this document, we will discuss the broad functionality of each component of the Portal Builder and provide links to additional resources that provide a more detailed discussion of specific tools provided by it. 


# Tree


The Tree is where you'll find an expandable and collapsible breakdown of the Portal associated with your application. Portals consist of individual Portal Pages, each of which can be designed around particular workflows or analytics requirements. 


The structure of the Tree is relatively uncomplicated. There are only two levels, and they nest as follows:


* Portal
  * Portal Pages


Portal Pages can be divided into two types: Data Grid and Embeds. New Portal Pages can be added by clicking the '+' icon to the right of the Portal.

<img src="./assets_v1714/portal-builder-v1714-1.gif" alt="organizing info" style="max-width: 350px; width:100%"/>


## Data Grid


[Data Grid Portal Pages](https://support.airkit.com/docs/the-structure-of-a-data-grid-portal-page) allow anyone accessing a Portal to view, modify, and otherwise interact with data stored in [AirData](https://support.airkit.com/docs/airdata). Once a Data Grid has been added to the Tree, the Stage and Inspector can be used to fine-tune exactly what data is displayed and how it can be interacted with.


## Embeds


Functionally, Airkit Embeds are Airkit web apps – but they are not necessarily the app you are modifying when accessing the Portal Page. Any app you publish in Airkit can be turned into an Airkit Embed, and any and all of your Airkit Embeds can turn into Portal Pages. (For more information on how to turn a published app into an Embed, check out [Airkit Embeds](https://support.airkit.com/docs/airkit-embeds).)


Through Embed Portal Pages, you can create endlessly customizable Portals. If you can design it as a web app, you can use it in a Portal Page.


# Stage


The Stage displays a visual representation of what will appear when a Portal Page is being accessed by a user.


## Data Grid


Data Grid Portal Pages display a table of data stored in AirData.


![2021-07-06_17-51-52.png](./assets_v1714/portal-builder-v1714-2.png)


Upon creation, Data Grid Portal Pages are blank and will display no data or table; the Inspector must be used to see the [App Object](https://support.airkit.com/docs/airdata-app-objects) that the Data Grid will display. By default, once an App Object is selected, the Data Grid will showcase all of the data associated with that App Object.


Should your use case require more precision in what is displayed, there are restrictions that can be applied to the data displayed, including:


* Designating the Data Grid as viewable to users with specific User Variables
* Removing unnecessary or un-important columns
* Only viewing data that matches an existing User Variable
* Showing deleted data


Some of these restrictions can be made directly in the Stage. For instance, to the right of each App Object property, you can apply filters to the value of each property. These filters will apply to all users that view the Data Grid. The results of any filter you apply will immediately be seen reflected in the Stage:

<img src="./assets_v1714/portal-builder-v1714-3.gif" alt="organizing info" style="max-width: 350px; width:100%"/>

By default, Data Grids also allow users the capacity to write and delete data, which is reflected in the Stage. Clicking the '+' icon on the bottom left of the Data Grid allows you to add data to the Data Grid. Selecting the checkbox to the left of the relevant App Object instance and clicking the 'Delete' button on the upper right will delete the row in question.


![2021-07-06_17-59-23__1_.gif](./assets_v1714/portal-builder-v1714-4).gif)


Further options to restrict how data is stored and displayed in Data Grids Portal Pages can be found in the Data Builder. See **Formatter/Parser** to learn more about how to modify the way that data is viewed and stored; see **Validation** to learn more about how to modify the way data is displayed.


## Embed


Embed Portal Pages display Airkit Embeds. In practice, this looks exactly like the UI of the app you have embedded. 


No changes to the embedded app can be made in the Portal Builder. All modifications to the embedded app must be made to the embedded app within the Studio. (And remember: Airkit embeds are Airkit web apps, but not necessarily the one you're modifying when accessing the Portal Page!) These changes must be published before they will be reflected here.


# Inspector


The Inspector is where you can examine and edit various aspects of your Portal Pages. Exactly which of these aspects are available depend on the type of Portal Page you are expecting.


## Data Grid


When examining a Data Grid, there are six expandable and collapsible sections that appear in the Inspector. Changes made in any of them will be immediately reflected in the Stage.


* **App Object** - Select which App Object to display in your Data Grid.


* **Data Flow** - Add buttons (these will appear to the upper right of the Data Grid) that allow Portal users to easily run [Data Flows](https://support.airkit.com/docs/data-flows) on the displayed App Object. For more information on how to do so, check out  [Running Data Flows from a Data Grid Portal Page](https://support.airkit.com/docs/running-data-flows-from-a-data-grid-portal-page).


* **Permissions** - Modify User Variables. User Variables serve as an additional means of security, as they limit access to Portal Pages to only users with accounts associated with precisely-matching pairs of User Variables and values. Note that User Variables and their associated values are case-sensitive. For more on how to associate User Variables with a user's account, check out [Adding Users to Airkit](https://support.airkit.com/docs/adding-users-to-airkit).


* **Properties** - Declare whether or not Portal users will have access to the button that allows them to delete data and whether or not certain filters will be applied to data added by Portal users.


* **Quick Filter** - Filter a single property so that it will display only the Default Value you provide.


* **Grid Edit State** - Set which properties of the displayed App Object are editable by Portal Users, or declare the entire Data Grid read-only. 


## Embed



Embed Portal Pages display Airkit Embeds, which are functionally Airkit web apps. No changes to embedded apps can be made within the Portal Builder. As a result, when inspecting an Embed Portal Page within the Inspector, the interface is relatively sparse: it contains only a single dropdown menu, allowing you to select which of your organization's Embeds will be displayed in the Portal Page.