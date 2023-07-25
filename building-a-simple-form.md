A simple form is a tool for collecting basic information from the user. It will contain a prompt for information and fields for the user to complete. Some good examples of simple forms are user sign-up or ticket information collection. This video starts with an introduction to a simple form that collects some user information and finishes by storing the data into [AirData](https://support.airkit.com/docs/working-with-data).


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FAoRcjWC5Q4Q%3Fstart%3D127%26feature%3Doembed%26start%3D127&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAoRcjWC5Q4Q&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FAoRcjWC5Q4Q%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=AoRcjWC5Q4Q&t=127s",
  "title": "Airkit 101 - Build Your First App in 10 Minutes",
  "favicon": "https://www.youtube.com/s/desktop/15c06292/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/AoRcjWC5Q4Q/hqdefault.jpg"
}
[/block]
### The basics of creating a form


The simplest example of a form is a single-page form. This form consists of one Web Page to collect data. Single pages forms are best for small amounts of data collection. It is recommended to break large collection processes into steps. For information on how to create multi-page forms, check out our documentation on [Web Flows](https://support.airkit.com/docs/web-flows). This section covers forms that have only a few input boxes, or for some reason must be on the same page (legal or otherwise).


This example creates a simple form for submitting an issue with a book delivery from the fictitious AirBooks Library. It will prompt the user for their name, and the issue they are having and allow a place for them to enter additional notes. Here is the basic app before any fields have been added.


![AirBooks-Empty.png](./assets_v1714/building-a-simple-form-v1714-0.png)


To start, add a [Container](ref:container-web-control) to the page, then put a [Label](https://support.airkit.com/docs/web-flows) and [Text Input](https://support.airkit.com/reference/text-input-web-control) inside the container. Change the text of the Label to "What is your name?". Text Inputs are used to collect smaller lines of text, like a name. When creating the Text Input, a Text Variable is created on the same Web Page as the input. Change the name by double-clicking the field, **string_input**, and change it to name. Note that changing the reference on the Web Page will update the associated value on the Text Input automatically.


Create another [Container](https://support.airkit.com/reference/text-input-web-control), insert a Label reading "How can we help you today?" and a [Text Area Input](https://support.airkit.com/reference/text-area-web-control). Text Area Inputs are used for larger blocks of text. In this case a description of what the customer is requesting. Click on the Web Page to change the bound value from **text_area** to **description**.


Lastly, add a [Button](https://support.airkit.com/reference/button-web-control) to the Web Page. Change the text on the button to "Submit". Buttons are used to perform [actions](https://support.airkit.com/docs/action-builder). In the case here, the button will submit the data that we have collected from the User.


The app should look something like this:


![Airbooks-Issue.png](./assets_v1714/building-a-simple-form-v1714-1.png)


How to submit form data
-----------------------


Once the customer information has been collected, it can be used in many different ways. For the purposes of this example, it will be used to create a Zendesk ticket. Before creating a Data Flow to create the ticket, the Zendesk Integration must be added to the App. Go to [Configuration Builder](https://support.airkit.com/docs/configuration-builder) and add a [Zendesk Integration](https://support.airkit.com/docs/zendesk-integration).


To send the data to Zendesk, go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and create a new [Data Flow](https://support.airkit.com/docs/data-flows), name it *ZD - Create Ticket From Customer Issue*. Add two Text Inputs to the connection in the Inspector, one called **name** and the other **description**. Inputs are a way of passing external information to the Data Flows. Data Flows exist in their own scope and do not have access to any of the other [variable scopes](https://support.airkit.com/docs/variable-scopes). The only way to get information into a Data Flow is to pass it in. Enter some test values for your input parameters in the stage of the Data Flow.


Select "Zendesk" from the drop-down on the Data Operation type. Select "Create Ticket" from the Operation drop-down. In the *Ticket Fields*set the Subject value to:



```javascript Airscript
"Support Request from {{name}}"
```

This is a line of Airscript, setting the Subject to a custom string using the input variable **name** to indicate who is making the request. Find out more in [Working with Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript). Put the **description** value in the Description field. Running this connection step will produce a Zendesk Ticket.


![SimpleFormZendeskRun.gif](https://a01-support.airkit.com/building-a-simple-form/SimpleFormZendeskRun.gif)


Looking at the payload from the response:



```javascript Airscript
{  
  "success": true,  
  "result": {  
    "ticket": {  
      ...  
      "subject": "Support Request from Molly Fey",  
      "raw_subject": "Support Request from Molly Fey",  
      "description": "I ordered a copy of the new Edward Tufte book and haven't recieved any shipping information yet. Might you be able to tell me when it will ship?",  
      ...  
    },  
    ...  
  },  
  "error": null  
}
```

The ticket has been created with the information passed in.


The last step is to connect the Data Flow to the Submit button on the form in App Builder. Select the Submit button, add a clicked Action. Under the "App" section, select the [Run Data Flow](https://support.airkit.com/reference/the-run-data-flow-repeatedly-action) action. Select the *ZD - Create Ticket From Customer Issue*data flow from the list. Pass in the **name** and **description**, respectively.


![AirBooks-SubmitAction.png](./assets_v1714/building-a-simple-form-v1714-2.png)


Running the App in Preview will submit a ticket every time the submit button is pressed. This is one example of how to use the data, but using an [HTTP Operation](https://support.airkit.com/reference/http-request-data-operation) it is possible to send this data to any external API.