One common interaction is to have a user select an item from a list. One such way to do this is with a dropdown list. This article will walk through two different ways to use dropdown lists. Either as a pre-programmed option list or a dynamic list from a set of data.



Creating an Option List
-----------------------


Option Lists are useful when the items in the list are known at the creation time of the app. For example, selecting a lead type for a new salesforce contact or selecting a t-shirt size on an ordering form. Let's build out the example to rate a book in the AirBooks app.


Start with a [Web Flow](https://support.airkit.com/docs/web-flows) with one page on it. Add a label of the large variant, set the text to "Enter Your Book Review:." Next, add a container with a label and a text input. Set the label equal to "Enter the book title." Add a new container with a label with the text "Select a rating." Next, add a Dropdown list under the picker option in the Add Control dialog.


With the dropdown selected, the inspector will have a section called *Data Binding*. This section is used to determine the items that will appear in the list and where the selected value will be stored. By default, when a dropdown is inserted into the Tree a variable is created to store the result. There are two options for dropdown list type: simple list, and custom expression. Simple list, also known as an option list, is where you configure the items in the UI.


Add five different items by clicking the + icon to the right of the options. Set the values to *1 Star, 2 Stars, 3 Stars, 4 Stars*, and *5 Starts*. In a simple list, when the user selects an option from the dropdown, that text value will be stored in the text variable.


![Screen_Shot_2021-04-04_at_7.02.22_PM.png](./assets_v1714/working-with-option-lists-vs-dynamic-lists-v1714-0.png)


Creating a Dynamic Dropdown list
--------------------------------


Whereas simple list drop-downs are great for known information, dynamic lists are great for use when the items in the list can be dynamically run generated at run time. These are also useful if the list will be populated from configuration information that may change over time. Let's say that in addition to letting the user rate the book, the user should be allowed to select the category of the book during the review.


Start by going to Data Builder and creating a new [App Object](https://support.airkit.com/docs/airdata-app-objects). Title it "Genre", rename the property from **Name** to **genre_title** and add options in Data Builder for the categories: "Youth", "Reference", "NonFiction", and "Mystery." Click save and click continue on the save dialog when it appears. It is simply saying that we are adding new data to the AirData Datastore attached to our app.


Go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and add a new Data Flow named "AD - Get genres." Modify the first Data Operation to be of type "Object-Service." Select the app object *Genre* from the dropdown. Make sure the type is QUERY. Click Run at the top of the step and confirm that the output contains the shelves you added above. Because the query run returns a complex object with a bunch of different options, add a transform step after the query. Set the body of the transform to:



```javascript Airscript
airData.results[*].genre_title
```

Return the result of the transform from the Data Flow.



```javascript Airscript
[  
  "Nonfiction",  
  "Mystery",  
  "Reference",  
  "Youth"  
]
```

Go to Web Builder and modify our book review page to add a container between Star Rating and the Review box. Add a label "Genre" and a dropdown list to the container. Instead of the simple option list, this box will be populated by the connection built above. Select the Web Page and add a variable called **genres** as a list of text.


With the Web Page still selected, go to the Actions tab in the inspector and add an action for Run Data Flow under the App Section in the Action Builder. Select *AD - Get genres* from the dropdown and the output binding to **genres**. 


Select the dropdown list in the shelf container. Under *Data Binding* look for the *Type of List* option. Change it from "Simple List" to "Custom Expression." Set the *Data* value of the expression to **genres** and the Display Text to **item**. Run the page in preview and see the example below.


![Screen_Shot_2021-04-05_at_10.02.29_AM.png](./assets_v1714/working-with-option-lists-vs-dynamic-lists-v1714-1.png)


To add another genre to the list, simply go back to the Data Builder and add another row for the "Science Fiction" genre. Notice how the list will automatically contain the new item.


Selecting multiple items from a list
------------------------------------


The dropdown list that has been covered so far is for selecting single items from a list. In the case where multiple items can be selected, using a list of checkboxes might be more appropriate. In the example above, perhaps a book is a Youth Mystery book.


Replacing the dropdown list with a checkbox list will allow for this multiple selections of Genres. Go to the container containing the genre dropdown and remove the dropdown list. Add a Checkbox List from the Add control dialog, it is under the Repeater section. Add a checkbox and a label to the checkbox cell. Select the Checkbox List and set the data to **genres**. In order to store the selected genres, go to the Page and add a variable typed list of text named **selected_genres**. On the Checkbox List set the value to **selected_genres**. Set the text of the label to **item**.


Preview the app:


![Airbooks-checkbox-genres.png](./assets_v1714/working-with-option-lists-vs-dynamic-lists-v1714-2.png)


When Dropdown lists are desirable
---------------------------------


### How Dropdowns compare to other list controls


Dropdowns are just one of several list selection controls in Airkit. The other major possibilities include Checkboxes and Radio Lists. Dropdown lists allow the user to select one item from a list of items. Dropdown lists do this in a relatively small amount of screen real estate. The list expands when the user interacts and only shows the selection after. Radio lists have similar behavior of selecting one item from a list, but display all items visually, even once selected. Checkboxes on the other hand display all items visually but allow for multiple items to be selected.


### Why should I use a dropdown?


Dropdowns help with screen space. Use a dropdown on a form where there are a bunch of options and the user must select one. Because the dropdown options are only visible when editing the control, if there are too many options a dropdown might not be the best solution. Scrolling through many items, especially on a mobile device, can be challenging for some users.


Further Reading
---------------


* Check out the [Checkbox Component](https://support.airkit.com/reference/checkbox-web-control) and the [Radio Component](https://support.airkit.com/reference/radio-button-list-web-control)
* For more information on the [Dropdown component](https://support.airkit.com/reference/radio-button-list-web-control)
* Learn more about [Working with AirData](https://support.airkit.com/docs/working-with-data)