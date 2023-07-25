It is possible to create forms that appear as the user enters input. This can be helpful to direct the user to the next input. In other cases, inputs are dependent on each other and need to be entered in a specific order. This article will walk through the basics of building out a form that displays new fields based on user input. When the user enters data in one field, the next field will appear.


Creating the form
-----------------


[Create a simple form](https://support.airkit.com/docs/building-a-simple-form) that looks like this:


![AirBooks-Review1.png](./assets_v1714/dynamic-forms-based-on-user-input-v1714-0.png)


Start by adding a [Container](https://support.airkit.com/reference/container-web-control) to the web page. This container will hold the entire input form. Create a [Label](https://support.airkit.com/reference/label-web-control) for the prompt. Create a container for the book title label and the [text input](https://support.airkit.com/reference/text-input-web-control). Create another Container for the star rating label and the input. Create a third container for the "write your review:" label and [text area input](https://support.airkit.com/reference/text-area-web-control). Create a submit button at the bottom. When completed, the Tree view should look like this:


![AirBooks-Review-Field_Tree.png](./assets_v1714/dynamic-forms-based-on-user-input-v1714-1.png)


Setting up inputs to appear in order
------------------------------------


Components in the studio have a property called *Is Visible*. This is an expression that evaluates to TRUE or FALSE. If the expression evaluates to TRUE, the component will appear, if the expression evaluates to FALSE, then the component will be hidden. The *Is Visible* is dynamically recalculated so if the value of the expression changes from FALSE to TRUE, the component will appear. Using this, it is possible to have components appear on the page.


Start by going to the container that has the star rating. With the container selected, choose the Advanced tab in the inspector. Put the following code snippet into the *Is Visible* option:



```javascript Airscript
ISNOTEMPTY(title)
```

Using [ISNOTEMPTY()](https://support.airkit.com/reference/isnotempty) will hide the entire container, including the label until the user enters a title for the book. To understand more about empty states, check out the [Airscript Empty States](https://support.airkit.com/docs/working-with-missing-values-with-airscript) article. Selecting the container for the review text area, set the *Is Visible* value in the Advanced tab to:



```javascript Airscript
ISNOTEMPTY(rating)
```

By putting visibility dependent on the rating, and the rating having the visibility dependent on the title, this field will start hidden, and only be displayed once the title and then the rating is selected. Modify the submit button in the same way by setting the *Is Visible* equal to:



```javascript Airscript
ISNOTEMPTY(  
  review_text  
) 
```

Running the experience in preview should look similar to:


![DynamicFormsBookReview.gif](https://a01-support.airkit.com/dynamic-forms-based-on-user-input/DynamicFormsBookReview.gif)


Submitting to the same page
---------------------------


While it is usually a best practice to space out a form experience through several web pages within a web flow, there are certain times where it might make sense to collect data on the same page. A page rendering search results is a good example of this pattern.


Create another container at the root of the Web Page containing the book review. Name it "Response Container". Add a Label to the container and enter some text like "Response Received". Click on the Web Page and a variable called **response_sent** of type Boolean. Then go back to the Response container and set the Is Visible to:



```javascript Airscript
response_sent
```

this variable. Select the Input container and set the Is Visible to:



```javascript Airscript
NOT(response_sent)
```

Go to the submit button. Add a Clicked action that sets the value of **response_sent** to [TRUE](https://support.airkit.com/reference/the-boolean-variable-data-type). Now when the flow is run it should look like this:


![Airbooks-Dynamic-InlineSubmit.gif](./assets_v1714/dynamic-forms-based-on-user-input-v1714-2.gif)


Refreshing the page
-------------------


What if the user wanted to submit another review. This section will walk through resetting the form. Go to the Response Container and add a button with the text "Write another review". Go to the Actions tab in the inspector for the button. Add four [Set Variable](https://support.airkit.com/reference/the-set-variable-action) actions for the Clicked event.


![AirBooks-Dynamic-AnotherReviewActionTree.png](./assets_v1714/dynamic-forms-based-on-user-input-v1714-3.png)


This is taking all of the inputs for the form and setting them back to the original starting point of the App, with all of them set to [**NULL**](https://support.airkit.com/reference/the-null-data-type). The final effect of the app is that once the user clicks the button to write another review, the Response Container will be hidden and the Input Container will be rendered. The fields are empty so the Input container will only have the book title container visible.


![Airbooks-Dynamic-ResetForm.gif](./assets_v1714/dynamic-forms-based-on-user-input-v1714-4.gif)


Further Reading
---------------


* [Validation](https://support.airkit.com/docs/validation-of-forms-and-user-data)
* [Working with Data Flows](https://support.airkit.com/docs/data-flows)
* [Working with external systems](https://support.airkit.com/docs/connecting-to-external-systems)