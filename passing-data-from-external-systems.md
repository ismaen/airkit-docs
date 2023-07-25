Inbound Requests with App APIs
------------------------------


There is also the ability to set up an API to allow Airkit to receive custom payloads where you can create journeys, modify existing journeys, or even get information back from journeys.  For steps on configuring inbound requests with App APIs, see [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app)


Inbound Requests with Subscriptions (web hooks)
-----------------------------------------------


### Understanding Subscription and Events


Subscriptions (webhooks) are a mechanism to send data when triggered by an event in an application. Within an Airkit application, you can set up subscriptions with the Airkit's first party integrations such as Twilio, Zendesk, Salesforce, Google, and Stripe. For example if you use the Salesforce Subscription, you can start a journey when a the status of a lead is updated or if a record is created. 


**Setting up a Subscription**


In this example, we'll be setting up a subscription to Salesforce whenever a Lead is added.


1. Before creating a subscription, [set up a connection to Salesforce](https://support.airkit.com/docs/create-a-salesforce-lead) and then add the integration to your Airkit Application. Once connected, go to **Configuration Builder**and add the Salesforce adapter in **Integrations.** Click on **+New** and then **Adapters,** and select **Salesforce**. 
  
![mceclip7.png](./assets_v1714/passing-data-from-external-systems-v1714-0.png)
2. Select the **Credential** associated with Salesforce that you would like to use and **Save**. This will enable your app to use the Salesforce integrations when creating a Subscription.   
  
![integrations.png](./assets_v1714/passing-data-from-external-systems-v1714-1.png)
3. Go to **Connection Builder** and click on '**+**' to add a Salesforce subscription.   
![mceclip12.png](./assets_v1714/passing-data-from-external-systems-v1714-2.png)
4. Select a webhook category. For this example, we'll be starting a journey when a new record is added.   
  
![mceclip13.png](./assets_v1714/passing-data-from-external-systems-v1714-3.png)
5. Choose an **Object Type**. This example will be using the Lead object type.   
  
![mceclip8.png](./assets_v1714/passing-data-from-external-systems-v1714-4.png)


After selecting the Object Type, you can define what happens after a lead is added by configuring the journey mapping.


  
**Configuring the Journey Mapping**


If you have [created an API for your Airkit App,](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app) then the journey mapping configuration may look familiar. 


#### Sample Payload


This is a sample so you can use to know how to build your request. After expanding the Sample Payload, you can hit the Play button to see what that payload would look like. 


![mappingmceclip0.png](./assets_v1714/passing-data-from-external-systems-v1714-5.png)

**Mapping**
The mapping section is where you can specify what happens once your subscription receives an event. For example, when a lead gets added into salesforce, you can:


* Start a new journey
* Replace a current journey
* Abort a journey if a match is found
* Lookup and use an existing journey


**Start Parameters **
![start-parameters.png](./assets_v1714/passing-data-from-external-systems-v1714-6.png)


Start parameters is where you can pass any type of data that is available from your subscription to the journey to **session.start.** Start parameters are only applicable when your **Journey Behavior** is 'Start or Create a new Journey'. 

```javascript Airscript
session.start
````


**Journey Identifier Expression**![mceclip2.png](https://a01-support.airkit.com/passing-data-from-external-systems/mceclip2.png)


The [journey identifier expression](https://support.airkit.com/docs/journeys) is where you can map an identifier on a session from a piece of data out of the payload or connection namespace. For example, if there was a specific Salesforce ID that came out of the request payload, you could then use that Salesforce ID as the journey identifier. You are given the options of what type the identifier is as well -- Text, Journey ID, or Phone. 


**Journey Event Payload**![mceclip3.png](https://a01-support.airkit.com/passing-data-from-external-systems/mceclip3.png)Journey event payload is where you can pass data from your subscription into the **event** namespace.


For example, if you pass



```javascript Airscript
payload.result
```

into the Journey event payload, then on your subscription event, you can access the data via



```javascript Airscript
event.property_name
```

**Response**
This is where you can define what your subscription will return after the actions are executed. 


Response Status is where you can perform validation using Airscript to have your subscription return a particular response status code. This example checks to see if the Phone property is empty, and returns a 200 if it is not empty. 


![mceclip0.png](./assets_v1714/passing-data-from-external-systems-v1714-7).png)


Response Body is the response from the subscription. The response body accepts data from the metadata, payload, and connection namespace. 


### How Publishing an App subscribes and unsubscribes from an external web hook


When publishing an app, the subscription (web hook) is set on the external system. So when creating the subscription, the subscription has not actually been registered yet until the app has been published. Alternatively, when the app is unpublished, the web hook is unset from the external system. 


Further Reading
---------------


* [Connecting to External Systems](https://support.airkit.com/docs/connecting-to-external-systems)
* [Receiving Inbound HTTP API Requests with your App](https://support.airkit.com/docs/receiving-inbound-http-api-requests-with-your-app)
* [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app)
* [Querying and Manipulating Data From External Systems](https://support.airkit.com/docs/querying-and-manipulating-data-from-external-systems)
* [Connecting Airkit to Your Systems](https://support.airkit.com/docs/setting-up-integrations)