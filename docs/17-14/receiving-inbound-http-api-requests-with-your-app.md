When configuring App APIs, you can manage the events that occur when an inbound request comes in. For example, if an App API receives a request, that request can be handled through the API event, which can trigger a [Data Flow](https://support.airkit.com/docs/data-flows), [start a chat/voice bot](https://support.airkit.com/reference/the-start-chat-bot-action), or any other action. This is useful because it allows you to handle the data from the API request however it is needed, and that data can be used throughout the journey.


This guide will cover how to handle an inbound API request and store that data into AirData. Prerequisites for this guide include the following:


* [An API has been created in Airkit](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app)
* An [App Object](https://support.airkit.com/docs/airdata-app-objects) has been created in AirData with the following properties: id, first_name, last_name
* User understands [Data Flows](https://support.airkit.com/docs/data-flows)


Create the App API
------------------


For this example, the App API will be configured as a POST request and the request body will look like the following:




```javascript Airscript
{  
  "id": "1001",  
  "first_name": "Michael",  
  "last_name": "Scott"  
}
```


This will be placed in the request body under the Sample URL, which is used to create a sample payload. When clicking the '**Play**' icon, this will generate a sample payload that can then be accessed through the '**payload**' namespace.
![mceclip0.png](https://a01-support.airkit.com/receiving-inbound-http-api-requests-with-your-app/mceclip0.png)
 
For information on how to create an App API, validation, mapping, and response codes, see [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app). 
 
Mapping the Request to a Journey Event
--------------------------------------


In order to map the API request to the journey, there are two approaches - passing the request to **session.start** or passing it to the journey event. This example will show how to pass the request body to the **event** namespace, but you can easily pass it to **session.start** by passing the payload to the 'Start Parameters' under the Mapping section of the API configuration. For further reading, [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app) includes a breakdown of each of the Mapping properties. 


Under the Mapping section, enter **payload.body** under Journey Event Payload. This will surface the request body in the API request handler event and allow you to access the id, first_name, and last_name from the payload. 


![mceclip0.png](https://a01-support.airkit.com/receiving-inbound-http-api-requests-with-your-app/mceclip0%20(1).png)


Creating the Data Flow to pass the request to AirData
-----------------------------------------------------


Once the API is set up, a Data Flow will need to be created to pass the request body to an App Object in AirData. The Data Flow created for this example will need to capture the id, first_name, and last_name and then write that to AirData.


Create a Data Flow and name it 'Insert User Object'. Add three text input variables. The request properties will be passed into the data flow inputs. 


![mceclip1.png](https://a01-support.airkit.com/receiving-inbound-http-api-requests-with-your-app/mceclip1.png)

Then add the [AirData data operation](https://support.airkit.com/reference/airdata-request-data-operation), select the App Object that you want to store the values to, and change the Type to **PUT**. Then in Objects to insert or update, add:




```javascript Airscript
[  
  {  
   "id":id,  
   "first_name":first_name,  
   "last_name":last_name  
  }  
]
```


The object service Data Operation should look like the image below:


![mceclip2.png](./assets_v1714/receiving-inbound-http-api-requests-with-your-app-v1714-0.png)


 


Running the Data Flow in the API event
--------------------------------------


Every API created in Airkit has an event associated with it. In the event, you have the option to run many different actions when that API endpoint receives a request. To add actions to the event, go to **Journey Builder** > **Integrations** > **App API** > Select the API you created > Go to the **Actions** tab in the inspector.  ![2021-03-31_11-25-59__1_.gif](./assets_v1714/receiving-inbound-http-api-requests-with-your-app-v1714-1).gif)


Go to **App** > Add the [Run Data Flow action](https://support.airkit.com/reference/the-run-data-flow-data-operation) and select the Data Flow created in the previous step. In the inputs, enter in the following:


* **id**: event.id
* **first_name**: event.first_name
* **last_name**: event.last_name


![mceclip4.png](./assets_v1714/receiving-inbound-http-api-requests-with-your-app-v1714-2.png)


Using the event namespace, you can access the data that was passed to the Journey Event Payload in the previous Mapping step. 


Now the application is set up to receive a POST request and will write the request body back to AirData. 


Additional Use Cases
--------------------


An inbound API can be used to trigger many different actions within Airkit. One use case, is to use that inbound API to initiate a chat conversation via SMS from an external system. For example, for tracking statuses, an external system can be used to call the inbound API to initiate a journey that sends an update to that user about their status being updated or changed. They can then be sent a 'canvas link' to view more details for what is being tracked within that SMS as well. 


Another use for an inbound API is to use it to change or update a web page on an existing session. For example, an inbound API can be mapped to an existing session and when an external system makes a request to that API, it can trigger an update to that user's session and take them to a new view. For example, this is useful for waiting on an external system to verify information of a user and will make a request back to the application once it is done verifying.


Further Reading
---------------


* [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app)
* [Securing API Endpoints with Airkit API Tokens & Permissions](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions)
* [Connecting to External Systems](https://support.airkit.com/docs/connecting-to-external-systems)