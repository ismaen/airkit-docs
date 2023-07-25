Another common use case in form development is the repetition of items from a collection. For example, selecting a house from a list of houses, or picking out a doctor from a list of practicing physicians. While it is possible to present this to the user with a dropdown list, there may be additional information associated with each of the options to present to the user. One such solution is to use Lists of options in a form.


Building Out a List
-------------------


Airkit’s repeaters make it easy to build repeatable content tied to lists of data. These repeaters can be used to display collections of content, but they can also be used to create dynamic, selectable content. Selecting a single house from a list of houses is a great example.


Building this out will require the use of a Checkbox List Component. For each house, let's show a house title, picture, square footage, bedroom count, bath count, and asking price. Users will be able to select the houses they are interested in.


Step one is to create some user data for the Houses object. Create a custom [AirData App Object](https://support.airkit.com/docs/airdata-app-objects) for the house with the fields **title** (text), **picture** (asset), **square_footage** (number), **beds** (number), **baths**(number), and **asking** (currency). Create a [Data Flow](https://support.airkit.com/docs/data-flows) to return all the houses from the table.


Create a new Web Flow. Add a web page. Add a title label with the text "Select the Houses you are interested in:" Add a [Checkbox List](https://support.airkit.com/reference/checkbox-list-web-control) and a submit button. 


On the Web Page create two variables of type List of Houses. Name one **houses** and the other **selected_houses.** Click on the Advanced Tab of the Inspector and add an action to run the Data Flow to put the entire house list into the **houses** variable.


Select the Checkbox List and set the value to **selected_houses**, set the Data field to **houses**, and the Selected Field to: 



```javascript Airscript
CONTAINS(  
  selected_houses,  
  item  
)
```

Using the [CONTAINS](https://support.airkit.com/reference/contains)() function this expression checks to see if the current house (the **item**) is in the collection of selected houses. The Checkbox list will take care of adding a selected house to the **selected_houses** array. 


Configure the checkbox cell to contain all the information in each house object. 


![Airhome-SelectMulti-CheckboxCell.png](./assets_v1714/repeating-elements-in-forms-v1714-0.png)


Lastly, it is time to configure the return value. Because of the way Checkbox Lists work, in order to send only the selected options to a Data Flow from the **selected_houses**, filter out the empty options:


![Airhome-HideShow-FilterNulls.png](./assets_v1714/repeating-elements-in-forms-v1714-1.png)


Putting this all together, the experience collects users selections and passes the selected values to the output data flow:


![Airhome-ListView-Final.gif](./assets_v1714/repeating-elements-in-forms-v1714-2.gif)


Further Reading
---------------


* [Querying Lists (Arrays) & Objects (JSON) in Airscript](https://support.airkit.com/docs/querying-lists-arrays-and-objects-json-in-airscript) to learn about filtering lists.
* [Checkbox List Web Control](https://support.airkit.com/reference/checkbox-list-web-control) to learn more about the properties of the checkbox list.
* [The Asset Data Type](https://support.airkit.com/reference/the-asset-data-type) for information on how to use the Asset Data type.
* [FORMAT_NUMBER](https://support.airkit.com/reference/format_number) is a helpful reference for displaying numbers in the table.