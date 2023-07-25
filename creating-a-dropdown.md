Introduction
============


Dropdown lists are a great way to allow a user to pick from a list of items, while keeping the UI elements to a bare minimum. In this article we’ll go over how to add and setup a dropdown list to your Airkit application.


This article assumes you’ve already reviewed how to create and edit applications in Airkit Studio.  
  



### Create your dropdown


Start by creating a new Airkit application (or editing an existing one):


1. Once your application is open in [Studio](https://studio.airkit.com/), go to the Web Page or Container you’d like to add a dropdown to.   
![mceclip0.png](./assets_v1714/creating-a-dropdown-v1714-0.png)
2. Click on the '**+**' button on your Web Page or Container to add elements to the card view, and select:  
*Container / Web Page → Dropdown List   
![dropdown_insert.gif](./assets_v1714/creating-a-dropdown-v1714-1.gif)*


  
Now that we have a dropdown, its possible to customize it's styling within **Inspector > Style**.  
There are a lot of ways to style a dropdown which we won't go into full-detail here, but below is a simple example where the Arrow has been made blue with a grey background.  
  
If you're interested in learning more about styling, we recommend looking at our documentation on [Themes and Control Variants](https://support.airkit.com/docs/working-with-themes-and-control-variants).  
  



![mceclip2.png](./assets_v1714/creating-a-dropdown-v1714-2.png)
3. Let’s dive in! The main properties' sections for a Dropdown list are: ![mceclip0.png](./assets_v1714/creating-a-dropdown-v1714-3).png)


	* Control Properties
	* Data Binding

**Control Properties**  
In the control properties section you can set up the *variable* you’ll be saving the selected option to (value) as well as the *text shown to the user* when no option has been selected (placeholderText).    
![1131544607.png](./assets_v1714/creating-a-dropdown-v1714-4.png)



`_variable_to_save.selection_to_` needs to be a valid variable i.e. it needs to exist within your application. If you are not yet sure of the _scope_ you need for your variable, it is ok to use _session_ while you build (not recommended for published apps): `session.variable_to_save.selection_to`


Please review your [variable scope](https://support.airkit.com/docs/variable-scopes) to make sure you’re using the appropriate variable scope.


1. **Data Binding**  
In the Data Binding section, you can control the data used to populate the dropdown list and how it’s displayed to the user.   
![1134985261.png](./assets_v1714/creating-a-dropdown-v1714-5.png)


*  **Data** is the List of items that will be shown as a list when opening the dropdown. You can hard-code a List or use a *[Data Flow](https://support.airkit.com/docs/data-flows)* to query an [*App Object*](https://support.airkit.com/docs/data-builder) and display a List. The above example displays contains a hard-coded List for the Dropdown.
*  **Display Text** is the value that reflects *what* will displayed.  In simple examples, the value should be "item" to reflect *each item* of the Collection / List provided to the Dropdown.
*  **Value Text** is the *value* that is saved when the app user selects an item from the Dropdown List.
*  **Selected** gives you the ability to control whether the value selected is displayed to the app user. This field evaluates an expression where if TRUE, will display the value to the app user.  For a more-detailed explanation, see [Dropdown List Control](https://support.airkit.com/reference/dropdown-list-web-control).