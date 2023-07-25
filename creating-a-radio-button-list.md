![2021-10-11_11-47-54__1_.gif](./assets_v1714/creating-a-radio-button-list-v1714-0).gif)


Radio Buttons allow a user to only select one item from a list. Using radio buttons are useful when only one item can and should be selected. This guide will walk through how to add a radio button to a web page.


Adding the Radio Button List Control
------------------------------------


With the Web Page selected in the tree, click on the '**+**' icon and add the [Radio Button List Control](https://support.airkit.com/reference/radio-button-list-web-control) to the web page. The Radio Button List control is located in the **Repeater** category. 


![mceclip0.png](./assets_v1714/creating-a-radio-button-list-v1714-1.png)


Configuring the Radio Cell
--------------------------


The Radio Button List Control comes preconfigured with a [Radio Cell](https://support.airkit.com/reference/radio-cell-web-control) nested in the list. The Radio Cell is a container where additional controls can be added to further customize the radio button experience. In this example, the Radio Cell will contain a [Radio Button](https://support.airkit.com/reference/radio-button-web-control) control and a [label](https://support.airkit.com/reference/label-web-control) to describe the item. 


With the RadioCell selected in the tree, click on the '+' icon and add the Radio Button Control.


![mceclip1.png](./assets_v1714/creating-a-radio-button-list-v1714-2.png)


Go to the inspector and under the property **Style** > **Distribute Children** change it to Stack Horizontal and make the arrangement to be **Center Left**.


**![mceclip6.png](./assets_v1714/creating-a-radio-button-list-v1714-3.png)**


Then add a Label control.


![mceclip2.png](./assets_v1714/creating-a-radio-button-list-v1714-4.png)


Click on the Label control in the tree and change the Text property to:



```javascript Airscript
item
```

This will pass the data from the Radio Button List to reflect in the label. 


![mceclip3.png](https://a01-support.airkit.com/creating-a-radio-button-list/mceclip3.png)


Adding a Web Page Variable
--------------------------


A variable is needed to store the value of the selected item from the radio button list. To add a variable, click on the web page in the tree, and click on the '+' icon in the inspector under **Variables**. Add a **text** variable type and call it **selected.**


**![mceclip4.png](https://a01-support.airkit.com/creating-a-radio-button-list/mceclip4.png)**


Configuring the Radio Button List
---------------------------------


Then, click on the Radio Button List in the tree and add a list of objects to the **Data** property under **Data Binding**. 




```javascript Airscript
[ "Apples", "Bananas", "Oranges" ]
```


Then add **item** to the **Value Text** property. Next, add **item = selected** to the **Selected** property. And under **Control Properties** > **Value**, add the **selected** variable. The properties on the Radio Button list should look like this:


![mceclip7.png](./assets_v1714/creating-a-radio-button-list-v1714-5.png)


After completing these steps, the Radio Button list should be functioning and the item selected is stored in the selected variable!


Additional
----------


This guide walked through how to manually create a radio button list. With [Kitcloud](https://support.airkit.com/docs/kitcloud), there is the Radio Button Cell Static template and the Radio Button Cell Dynamic template that will automatically create a radio button list for you in a separate [web flow](https://support.airkit.com/docs/web-flows). These can be found in the **Training** Category of Kitcloud when you create a new Web Flow. 


![mceclip8.png](./assets_v1714/creating-a-radio-button-list-v1714-6.png)