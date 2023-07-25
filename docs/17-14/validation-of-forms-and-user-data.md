Validation is the process of checking user input to ensure it matches the expectations of the app. Airkit provides multiple options for validation. 

Validating on Submit
--------------------


### Simple Length Validation


Validation of input is a common use case. In Zendesk, for example, it would not make sense to submit a ticket without a Title or Description as they are required. Validation can be used to confirm the existence of data as well as the format of data. Validation can be used to ensure a value is a number, string, or even an email address. Starting from the example in [Creating a Simple Form](https://support.airkit.com/docs/building-a-simple-form), entering an empty description would be an API issue, forgetting to enter a name would leave our Subject rather useless. The ideal scenario is to check for the existence of these fields on the user clicking the submit button. Do this by adding to the [Actions](https://support.airkit.com/docs/action-builder) for the Submit buttons [Clicked](https://support.airkit.com/docs/action-builder) Event, which will be fired when the user clicks on the button. 


Create boolean variables on the Web Page for **empty_title** and **empty_description**. On the clicked action of the button set the value of the variable based on calling **ISEMPTY()** on the **title** and the **description** property. The actions should look like this:


![Airbooks-NameEmptyCheck.png](./assets_v1714/validation-of-forms-and-user-data-v1714-0.png)


Add a [Condition Action](https://support.airkit.com/reference/the-condition-action) to the Action Tree enter the following in the condition box:



```javascript Airscript
NOT(  
  empty_name  
)  
AND NOT(  
  empty_description  
)
```

Put success actions below the *IF* statement. This will prevent the user from submitting a ticket with an empty message, but there is no information on the screen to explain why. Go back to the containers for *Name* and *Description* and add an error message. Under the Advanced tab in the Inspector, we will set the value of *Is Visible* to the value of the correct empty boolean for the field.


When the user clicks the submit button, if they have not entered a Title or Description, they will be presented with these error messages and know what to do before they attempt to submit again.


![Airbooks-EmptyDescription.png](https://a01-support.airkit.com/validation-of-forms-and-user-data/Airbooks-EmptyDescription.png)


This is a simple example of working with data validation based on length.


### Type Verification


In addition to checking for the presence of a field, it is possible to check the validity of the data in the field. This is particularly useful when the input coming from the user must fit a certain format. For example, when an email is required to look up related information. Building on the Airbooks example. Create a Web Flow for collecting an email address from the user. 


![AirBooks-EmailCheck.png](https://a01-support.airkit.com/validation-of-forms-and-user-data/AirBooks-EmailCheck.png)


To check for a valid email address, go to the Actions Tab in the Inspector for the Find Tickets button. Add a *Set Variable* action for checking the validity of the email. Use the function [ISEMAIL](https://support.airkit.com/reference/isemail)() to check the validity of the email. Then add a condition. If the email is valid, perform the successful action. The Action Tree should look like this:


![AddressBook-IsEmail-_ActionTree.png](https://a01-support.airkit.com/validation-of-forms-and-user-data/AddressBook-IsEmail-%20ActionTree.png)


ISEMAIL() is just one of the pre-packaged validation functions in Airscript. This pattern will also work with functions like:


* [ISEMPTY()](https://support.airkit.com/reference/isempty) and [ISNOTEMPTY()](https://support.airkit.com/reference/isnotempty)
* [ISEVEN()](https://support.airkit.com/reference/iseven) and [ISODD()](https://support.airkit.com/reference/isodd)
* [ISPHONE()](https://support.airkit.com/reference/isphone)
* [ISSTRING()](https://support.airkit.com/reference/isstring)


One additional note, **invalid_email** is used instead of trying to prove that email is valid using a [NOT](https://support.airkit.com/reference/not)(). This is because Airkit treats a NULL as false so by using a negative there is no requirement to set the state Page Added action of the initial Page.


### Custom Validation Requirements


Sometimes Validation requires business-specific, domain, knowledge. For example, trying to find a book by ISBN number. ISBN Numbers start with the letters "ISBN" and contain 13 digits of numbers broken up by dashes. An example of a valid ISBN is:



```javascript Airscript
ISBN 989-0-7267-9020-3
```

Create a simple page for gathering an ISBN:


![AirBooks-ISBN-Collectin.png](./assets_v1714/validation-of-forms-and-user-data-v1714-1.png)


Because checking validation on an ISBN is more complex, custom Airscript will be required. Instead of using ISEMAIL(), set the value of **invalid_isbn** to:



```javascript Airscript
NOT(  
  STRING_FIND(  
    activity.isbn,  
    "ISBN"  
  )  
  = 0  
  AND LENGTH(  
    STRIP(  
      activity.isbn,  
      "ISBN -"  
    )  
  )  
  = 13  
)
```

This snippet checks that text variable **isbn** starts with the letters "ISBN" and contains 13 characters that aren't those letters, space, or a dash. Starting with [STRING_FIND](https://support.airkit.com/reference/string_find)(), the code checks to see if the first address of the text "ISBN" is at index 0 in the text the user entered. If that passes the snippet strips all instances of the characters "I", "S", "B", "N", " ", and "-" from the input using the [STRIP](https://support.airkit.com/reference/strip)() function. It then confirms that the length of the remaining characters is 13. This is a particular example of [working with text](https://support.airkit.com/docs/working-with-text-in-airscript) in Airscript.


### Moving Complex Validation to a Connection


While the above example provides some basic checking for the ISBN, it does not cover all of the edge cases a user may enter into the search box. These ISBNs would all pass the validation above:



```
ISBNISBNISBNISBNISBN 989-0-7267-9020-3  
ISBN 989-0- ISBN 989-0-7267-9  
ISBN 989-0-7267-9020-3 ISBNISBN----
```

This validation is relatively simple. It can be made more complex to check by adding additional checks for overall string length, the validity of the numbers (for example, the first triplet must be either 978 or 979), or re-occurrence of the string ISBN. While it is possible to do this inline in the Action tree for the clicked action, it sometimes makes sense to pull this out into Data Flow to check for validity. Doing so can allow reuse of this check in other places in the App, or even just split complex validation into steps that can be more easily understood. This Flow will take in a Text variable that is the potential ISBN and return **true** or **false** based on whether the ISBN passes validation.


Go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and create a Data Flow, name it "Validation - is ISBN valid". Give it an input variable of type text with the name **potential_isbn**. Change the type of Data Operation of the first step to Transform. Copy and paste the validation code from the above check. Change the output of the Transform to type **Boolean**. Set the Return Value of the Data Flow in the End block to the output of the transform.


Go back to [Web Builder](https://support.airkit.com/docs/web-builder). Add a web page boolean variable called **valid_isbn**, then go to the Actions Tab for the "Find Book" button. Add a new [Run Data Flow](https://support.airkit.com/reference/the-run-data-flow-data-operation) under the Clicked Action. Select the "Validation - is ISBN valid" option and pass it in the **isbn** variable. Set the output of the flow to **valid_isbn**. Click and drag this operation to the top of the action Tree.  Clicking the add icon next to the condition block, add an ELSE block, and set the value of **invalid_isbn** to TRUE.


At this point, this version replaces the inline Airscript with a connection. While this hasn't improved the quality of the validation, it has moved it to a Data Flow for potential reuse throughout the App. 


### Breaking up the Validation in the Data Flow


Go back to Connection Builder and select the data flow. Add a new Data Operation right after the Start. Select *Transform* from the type dropdown. In the transform step put in the following:



```javascript Airscript
STRING_FIND(potential_isbn, "ISBN") = 0
```

Change the output type of the transform to **Boolean**. Change the name of the output in the Inspector to **starts_with_isbn**. Next, create another Data Operation. Choose Transform from the Type dropdown and paste in the following code:



```javascript Airscript
SUBSTRING(potential_isbn, 5)
```

This is taking the ISBN of the format "ISBN 989-0-7267-9020-3" and removing the "ISBN " from the beginning. The text "989-0-7267-9020-3" will be stored in the output of this transform.


Set the return type of the Data Operation to Text and change the name in the Inspector to **isbn_numbers**. 


Add an operation to check the length validity of this section in terms of numbers. Create another Data Operation. Select type *Transform.* Enter the following code in the Transform Expression:



```javascript Airscript
LENGTH(STRIP(isbn_numbers, " -")) = 13
```

Set the output to type **Boolean** and name it **valid_length**. Let's add one more step to ensure that the first set of numbers is either 978 or 979. Create another Transform Data Operation. Enter the following code in the Transform Expression:



```javascript Airscript
SUBSTRING(isbn_numbers, 0, 3) = "978"  
OR SUBSTRING(isbn_numbers, 0, 3) = "979"
```

Set the output to type **Boolean** and rename the output to **correct_starting_code**.


Now that all the steps are set up, it's time to perform the final validation. In the last step (the one that is leftover from the previous example), paste in the following code:



```javascript Airscript
starts_with_isbn AND valid_length AND correct_starting_code
```

Because our Data Flow returns if the item is invalid, start with the expression that returns valid. If the text starts with ISBN, is a valid length, and has the correct starting code it is valid. If any of those aren't true, the ISBN is invalid, which means the response to a connection asking if the ISBN is invalid would be **TRUE**.


Testing this out with the inputs we described above:


![Airbooks-ConnectionValidation.gif](./assets_v1714/validation-of-forms-and-user-data-v1714-2.gif)


This example is relatively contrived, but as validation gets more and more complex, breaking it into Data Flows makes it easier to understand for the people maintaining the App.


Inline validation
-----------------


All of the previous examples have dealt with validation at the time of clicking on the submit button. While this is usually good enough, sometimes you will want to check validation as the user is typing into the input box and display helpful messages. Going back to the email ticket lookup example. It is possible to let the user know that their input is invalid as they are typing. 


Go to the error message for the invalid email on the enter email web page and select the Advanced tab in the inspector. Modify the value of the IsVisible property to be:



```javascript Airscript
ISNOTEMPTY(email) AND NOT(ISEMAIL(email))
```

This is saying that if the email variable (which is updated whenever the user types into the string input) is not empty and does not have a valid email display the message. Once the user's email becomes a valid email format, the error message will disappear.


![InlineValidation.gif](./assets_v1714/validation-of-forms-and-user-data-v1714-3.gif)


This pattern will work for most of the validation techniques above. Because it is not possible to call a connection on the input of a text field, currently it is not possible to use the Data Flow validation in this manner.


Further Reading
---------------


* [Airscript Examples](https://support.airkit.com/docs/airscript-examples)
* [Creating forms & agreements](https://support.airkit.com/docs/working-with-forms-and-agreements)
* [Data Flows](https://support.airkit.com/docs/data-flows)