In [Working with Option Lists vs Dynamic Lists](https://support.airkit.com/docs/working-with-option-lists-vs-dynamic-lists) the picker dropdown list was used with simple objects like a list of genres. In the custom list examples, for custom expression, the list was simply text. Sometimes, the data will be more complex. Sometimes one dropdown selection will determine the values in the next. This article will cover how to use dropdown lists with more complex data.


Configuring a dropdown to select a Salesforce Contact
-----------------------------------------------------


Salesforce contacts are complex objects. Using some Airscript, it is possible to populate a dropdown list to select a Salesforce contact. See [Additional Reference](https://support.airkit.com/docs/complex-objects-in-a-dropdown#additional-reference) for more information on a mock salesforce contact. 


This example assumes a connection to a Salesforce instance with an integration. To configure your Salesforce Instance, check out [Creating a Salesforce Lead](https://support.airkit.com/docs/create-a-salesforce-lead) for information on how to connect a Salesforce integration.


Go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and create a new Data Flow. Name it "SF - Get Contacts". Change the data operation to type "Salesforce." Select the Salesforce Datasource, and select "Find Records" for the operation type. Choose Contact (Contact) for the *Object Type.* Add several fields, make sure Full Name is included. Run the operation and the step should return data in the format:



```javascript Airscript
{  
  "success": true,  
  "result": [  
  {  
    "Id": "0034x000007Ro68AAC",  
    "AccountId": "0014x000009psYGAAY",  
    "LastName": "Gonzalez",  
    "FirstName": "Rose",  
    "Name": "Rose Gonzalez",  
    "Salutation": "Ms.",  
    "MailingStreet": "313 Constitution Place\nAustin, TX 78767\nUSA",  
    ...
```

Because the list of contacts is in the **result** property of the Salesforce response, create another Data Operation of type Transform. Insert the following snippet into the transform box:



```javascript Airscript
Salesforce.result
```

This strips the extra return information from Salesforce and just returns the data in the form of a list of results. Return the **transform** from the Data Flow.


Go to Web Builder and create a new Web Flow. Name it "Corporate Buyers Program." Create a Web page and add a heading label with the text "Corporate Buyer's Club:" Add another label with the text "Select the account point person:" Create a dropdown list from the picker list of controls. Lastly add a submit button. The page should look something like this:


<img src="./assets_v1714/complex-objects-in-a-dropdown-v1714-0.png" alt="Drop down" style="max-height:300px"/>


To connect this to the Data Flow, select the Web Page. In the inspector Add a variable **contacts** of List of Any type. Create a second variable called **selected_contact** of type Any. With the page still selected, under the Actions tab add a [Run Data Flow](https://support.airkit.com/reference/the-run-data-flow-action) action to the "Card Updated" event. Set the action the "SF - Get Contacts" data flow and set **contacts** for the output variable. This will populate the variable at the time the card is first created.


Select the Dropdown List. In the Data Binding section, change the "Value" to a custom expression and enter **selected_contact.** This will store the currently selected contact with all of the fields. Change "Type of List" to *Custom Expression.* For Data select contacts. This will use the list returned from the Data Flow. Set the display text to **item.Name**. This is the text that will display for each item in the dropdown list. For "Value Text", put in **item**. This will put the entire contact record into **selected_contact**. For the "Selected" field, insert:



```javascript Airscript
selected_contact.Id = item.Id
```

This expression will evaluate to true if the item has the same **Id** as the selected contact's **Id**. This is more reliable than checking on Name because it is possible to two contacts to have the same name, but not the same Id. The configuration of the dropdown should look like this:




<img src="https://a01-support.airkit.com/complex-objects-in-a-dropdown/Airbooks-CustomDrop-DropdownConfig.png" alt="Airbooks-CustomDrop-DropdownConfig.png" style="max-height:350px"/>



Save, configure the launch trigger and run in Preview. Interaction with your dropdown should be similar to the following:




<img src="https://a01-support.airkit.com/complex-objects-in-a-dropdown/Airbooks-Dropdown-CustomObj.gif" alt="Airbooks-CustomDrop-DropdownConfig.gif" style="max-height:350px"/>


Note that even though the example is just selecting the contact's name, the actual value of **selected_contact** is the full Salesforce contact. This means that **selected_contact** will have all the additional properties selected from the original object.


Working with complex objects and dynamic dropdowns
--------------------------------------------------


If a dropdown list becomes too large, it can be difficult for users to find the exact item they are looking for. It can be easier to group items into a category and allow the user to specify the item within that category.


To demonstrate this let's build a simple example of a towing app. This will ask the user for the Make of a car first then display the items within the make.


Go to [Data Builder](https://support.airkit.com/docs/data-builder) and add a new AirData App Object named "Car." Give it text properties of "Make", "Year", and "Model." Populate the AirData table with some data. Click save and click "Continue and Save" on the migration dialog.


Go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and create a new Data Flow named "AD - Fetch cars." Select the AirData option from the Data Operation dropdown. Select Car from the "App Object" dropdown. Leave type query, select paginate and run the operation. Add a transform after to return only the results:



```javascript Airscript
objectService.results
```

Go to [Web Builder](https://support.airkit.com/docs/action-builder) and create a new Web Flow. Create a new web page and add a label and a dropdown. Set the label to text to "Select Your Vehicle:" Select the web page and add a variable for **all_cars** with the type List of Car, add another variable **selected_car** with type Car.


Select the Dropdown List. Change the value of the Data Binding Value to "Custom Expression" and enter **selected_car**. Set the "Type of List" to *Custom Expression*. Fill in the values:


| Data | Designation |
|--------------|--------------------------------------------------|
| All Data         | **all_cars**                                     |   
| Display Text | ` "{{item.make}} {{item.model}} {{item.year}}" ` |   
| Value Text   | **item**                                         |   
| Selected     | ` item.__id = selected_car.__id `                |   

The **.__id** property is how the AirData table uniquely identifies each row. It is possible to use it here as a unique identifier for each row rather than comparing the make, then model, then the year.


Preview the app. Notice how long the list is with all the options are:


<img src="./assets_v1714/complex-objects-in-a-dropdown-v1714-1.png" alt="Airbooks-CustomDrop-DropdownConfig.png" style="max-height:350px"/>


Depending on the list of cars supported, the user could be scrolling for a very long time to find their car. This process can be improved by changing this one dropdown to three separate dropdowns, one for Make, one for Model, and the last for a year.

Create a new Web Flow. Create a new Web Page. Add a container with a label and a dropdown. Set the text of the label to "Select a make:." Select the Web page and add the following variables:


| Variable Name | Variable Type |
|--------------------|-------------------|
| **all_cars**       | List of Car |
| **selected_make**  | Text        |
| **selected_model** | Text        |
| **selected_car**   | Car         |

Select the Dropdown and set the value to **selected_make**. Change the "Type Of List" to *Custom Expression.* Set "Data" equal to:



```javascript Airscript
FROM  
  car  
IN  
  all_cars  
SELECT DISTINCT  
  car.make
```

This is using a Query Expression to pull out all the distinct makes from the list of **all_cars**.


Repeating the step for Model. Create a container with another label and dropdown. Set the text of the label to "Select a Model:." Set the value of the dropdown list to an Expression with the **selected_model** value. Change the list type to "Custom Expression"  and set the Data to:



```javascript Airscript
FROM  
  car  
IN  
  all_cars  
WHERE  
  car.make = selected_make  
SELECT DISTINCT  
  car.model
```

Change the "Selected" option to **selected_model = item**. Because the model can only be used once the make has been selected. With the container selected to the Advanced tab in the inspector and set "Is Visible" to **ISNOTEMPTY(selected_make)**. This will keep the user from selecting a model without having first selected a make.


Create one more container for the year. Add a dropdown and a label. Set the label text equal to "Select a Year:". Change the Dropdown's Data Binding value to **selected_car**. Set the Data to:



```javascript Airscript
FROM  
  car  
IN  
  all_cars  
WHERE  
  car.make = selected_make  
  AND car.model = selected_model  
SELECT DISTINCT  
  car
```

Set the display text to **item.year**. Set the value text to **item**. Set the "Selected" to **selected_car.__id = item.__id**. Because this is the final dropdown, the entire car is selected in the **selected_car**, whereas in the previous examples, only the value was selected. This will allow access to all properties on the car in the rest of the page. The properties on the data section for the Dropdown should look like:

  

<img src="https://a01-support.airkit.com/complex-objects-in-a-dropdown/AirTow-SelectedCarDropDown.png" alt="Airbooks-CustomDrop-DropdownConfig.png" style="max-height:350px"/>



Because the value year is not able to be selected until both the make and model are selected, set the visibility on the container for the year to:



```javascript Airscript
ISNOTEMPTY(  
  selected_model  
)  
AND ISNOTEMPTY(  
  selected_make  
)
```

Now the flow should work as desired:



<img src="./assets_v1714/complex-objects-in-a-dropdown-v1714-1.png" alt="Airbooks-CustomDrop-DropdownConfig.png" style="max-height:350px"/>


Additional Reference
--------------------


**Mock Salesforce Contact**


Example of a mock Salesforce Contact Record:



```javascript Airscript
{  
  "attributes": {  
    "type": "Contact",  
    "url": "/services/data/v45.0/sobjects/Contact/0035Y00003p12fmQAA"  
  },  
  "Id": "0035Y00003p12fmQAA",  
  "IsDeleted": false,  
  "MasterRecordId": null,  
  "AccountId": "0015Y00002cnHiUQAU",  
  "LastName": "Gonzalez",  
  "FirstName": "Rose",  
  "Salutation": "Ms.",  
  "Name": "Rose Gonzalez",  
  "OtherStreet": null,  
  "OtherCity": null,  
  "OtherState": null,  
  "OtherPostalCode": null,  
  "OtherCountry": null,  
  "OtherLatitude": null,  
  "OtherLongitude": null,  
  "OtherGeocodeAccuracy": null,  
  "OtherAddress": null,  
  "MailingStreet": "313 Constitution Place\nAustin, TX 78767\nUSA",  
  "MailingCity": null,  
  "MailingState": null,  
  "MailingPostalCode": null,  
  "MailingCountry": null,  
  "MailingLatitude": null,  
  "MailingLongitude": null,  
  "MailingGeocodeAccuracy": null,  
  "MailingAddress": {  
    "city": null,  
    "country": null,  
    "geocodeAccuracy": null,  
    "latitude": null,  
    "longitude": null,  
    "postalCode": null,  
    "state": null,  
    "street": "313 Constitution Place\nAustin, TX 78767\nUSA"  
  },  
  "Phone": "(512) 757-6000",  
  "Fax": "(512) 757-9000",  
  "MobilePhone": "(512) 757-9340",  
  "HomePhone": null,  
  "OtherPhone": null,  
  "AssistantPhone": null,  
  "ReportsToId": null,  
  "Email": "rose@edge.com",  
  "Title": "SVP, Procurement",  
  "Department": "Procurement",  
  "AssistantName": null,  
  "LeadSource": "Trade Show",  
  "Birthdate": "1969-02-19",  
  "Description": null,  
  "OwnerId": "0055Y00000F9t8fQAB",  
  "CreatedDate": "2021-03-09T17:17:51.000+0000",  
  "CreatedById": "0055Y00000F9t8fQAB",  
  "LastModifiedDate": "2021-03-09T17:17:51.000+0000",  
  "LastModifiedById": "0055Y00000F9t8fQAB",  
  "SystemModstamp": "2021-03-09T17:17:51.000+0000",  
  "LastActivityDate": null,  
  "LastCURequestDate": null,  
  "LastCUUpdateDate": null,  
  "LastViewedDate": null,  
  "LastReferencedDate": null,  
  "EmailBouncedReason": null,  
  "EmailBouncedDate": null,  
  "IsEmailBounced": false,  
  "PhotoUrl": "/services/images/photo/0035Y00003p12fmQAA",  
  "Jigsaw": null,  
  "JigsawContactId": null,  
  "CleanStatus": "Pending",  
  "IndividualId": null,  
  "Level__c": "Primary",  
  "Languages__c": "English"  
}
```

Further Reading
---------------


* Learn about [Simple List vs Custom Dropdowns](https://support.airkit.com/docs/working-with-option-lists-vs-dynamic-lists)
* Learn more about the [Query Expression Syntax](https://support.airkit.com/docs/filtering-data-using-query-expression)
* Learn more about [working with data](https://support.airkit.com/docs/working-with-data)