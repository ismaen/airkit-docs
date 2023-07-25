In complex forms, branching and different views are sometimes required. Typically, data drives the decision as to which branch to take. In Airkit, this is called form personalization. Data can be used to determine which aspects of a form to render, the order in which they are rendered, and what data is presented to the user on the page.


This article covers how to handle incoming user information in the form of a salesforce contact, but similar could be set up for interaction with a subscription to a [Zendesk](https://support.airkit.com/docs/zendesk-integration), [App API](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app),  or [another hook](https://support.airkit.com/docs/passing-data-from-external-systems).


Working with a Salesforce Contact
---------------------------------


Data can be provided to an Airkit app in a variety of ways. A common example is to connect Salesforce Data to Airkit. Salesforce data contain specific information about the customer, which makes them a great piece of data to use to personalize an app. Airkit Apps can be configured with a Salesforce Subscription, which can create new Airkit Journeys based on the subscription configuration. For more information about Salesforce Subscriptions [go here](https://support.airkit.com/docs/passing-data-from-external-systems). The examples within this article will assume that you have access to a Salesforce Contact available at **session.userInfo**. For full details of all the data contained within a Salesforce Contact, please check [this reference](https://support.airkit.com/docs/passing-data-from-external-systems).


Configuring UI Based on User Info
---------------------------------


Go to Web Builder, create a Web Flow and add a web page to the flow. Add a label and set the text to:



```
"Hello, {{  
  session.userInfo.Salutation  
}} {{  
  session.userInfo.LastName  
}}"
```

Set the variant to *largeHeadline.* Save the app. Add any additional information you would want to add the page. Hit preview and start the web journey. The result should look something like this:


![Screen_Shot_2021-04-04_at_4.05.14_PM.png](./assets_v1714/form-personalization-v1714-0.png)


This is a personalized screen for Ms. Gonzalez about the property, using data gathered at the start of the journey.


Configuring the Page UI Based User Info
---------------------------------------


It is possible to show pieces of UI contingent upon information gathered at the start of a journey. Go to Configuration Builder and update the information on the user data. Change the "Birthdate" field value to the current date, for example, "2021-04-04" for April 4th, 2021. 


Go to Web Builder and select the card from above. Add new container with a label inside that reads "Happy Birthday." Move this container to the top of the card. With the container selected, under the Advanced tab in the Inspector, enter the following into *Is Visible:*



```javascript Airscript
STRING_COMPARE(  
 FORMAT_DATE(  
 DATE_FROM_DATETIME(  
 NOW()  
 ),  
 "YYYY-MM-DD"  
 ),  
 session.userInfo.Birthdate  
) = 0
```

This snippet getting the current datetime from now, converting it to a date, formatting it as a string of the format four-digit year, dash, 2 digit month, dash two digit day. It then compares this string to the Birthdate field in the **userInfo.Birthdate** field. If they are equal, the box will appear, if they are not, the happy birthday box will not. 


Configuring the UI Based on user type
-------------------------------------


Changing content within a container won't always be sufficient, sometimes a different flow is required. For the example above, if the user was looking at getting insurance through AirHome, there might be completely different experiences for users who own their home vs those who rent their home. Homeowners will need to know additional information about the building, whereas renters are insuring their possessions and the structure or land.


Start by going to Web Builder and creating two Web Flows, named "Renter Flow" and "Purchaser Flow." Set them up to look roughly like this: 


![Airhome-Purchaser.png](https://a01-support.airkit.com/form-personalization/Airhome-Purchaser.png)![Airhome-Renter.png](https://a01-support.airkit.com/form-personalization/Airhome-Renter.png)


Go to Connection where the userInfo is returned and set the value of "LeadSource" to "Home Purchase."


Go to Journey Builder, Add a new [Condition Statement](https://support.airkit.com/reference/the-condition-action) from the Action Builder on the *Journey Started* event. In the condition box enter: 



```javascript Airscript
session.userInfo.LeadSource = "Home Purchase"
```

Add a [Go To Web Flow](https://support.airkit.com/reference/navigate-to-web-flow-action) action under the condition, select the "Purchaser Flow" from the drop-down list. Clicking the + icon on the condition, add an else clause. Add another Go To Web Flow and select the "Renter Web Flow" from the drop-down. The action tree should look like this:


![Screen_Shot_2021-04-04_at_5.02.39_PM.png](./assets_v1714/form-personalization-v1714-1.png)


Previewing the app will currently the Purchaser Flow. If the text for Lead Source is modified to anything else, We will show the renter flow. 


Further Reading
---------------


* [Creating APIs to your app](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app)
* [Subscriptions to external systems](https://support.airkit.com/docs/connecting-to-external-systems)
* [Working with Dates in Airscript](https://support.airkit.com/docs/working-with-date,-time-and-datetime-in-airscript)