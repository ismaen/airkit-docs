Introduction
------------


Sometimes you need to interact with your Application or its data outside of Airkit. With Airkit's Application APIs, you can build custom API endpoints for an application that allow you to create journeys, modify existing journeys, or get information back from journeys.


This is a tutorial for creating an API for an [Airkit Application](https://support.airkit.com/docs/passing-data-from-external-systems).



Add Web Resource to org
-----------------------


Before starting, a URL resource is required to be set up in order to be utilized by the API. Go to [console.airkit.com](http://console.airkit.com), go to [Resources](https://support.airkit.com/docs/adding-and-modifying-resources) (left-hand side nav), and create a new resource by clicking the “**New**” button. The URL resource will have to be configured depending on the scenario - for this example, the configuration looks like this:


![mceclip0.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-0.png)


This will generate a url that will serve as the API endpoint. For this example, that endpoint will be <https://app.airkit.com/c/AppApi>. 


Creating a Token
----------------


If the app API requires Authentication and should not be publicly available, a token must be created. For more information see [Securing API Endpoints with Airkit API Tokens & Permissions.](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions) For this you will need an API key that can be generated from the studio console (API > Tokens):


![2021-03-30_15-40-53__2_.gif](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-1).gif)


Important: make sure to safely store the generated token at that moment since it will not be retrievable afterwards.


Configure HTTP resource in Configuration Builder
------------------------------------------------


Once the URL resource is created you will need to configure it in your app. Open the app in the studio, and navigate to [Configuration Builder](https://support.airkit.com/docs/configuration-builder), and scroll down to the Integrations section.


Create a new “HTTP resource” connector: set any name that is meaningful , and under the Credential dropdown, select the URL resource created in the previous step.


![mceclip1.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-2.png)


Create App API
--------------


### Creating an API request handler / Endpoint


This section will provide an overview on how to create and configure an endpoint, this is, a specific route within an app that can be invoked externally and that can handle certain types of operations.


To create an endpoint within an app, go to [Connection Builder](https://support.airkit.com/docs/connection-builder) > Web Links, and click on the Plus (**+**) button. Then select HTTP Request.  
![mceclip2.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-3.png)


The http method can be **GET** or **POST**. Typically, GET is to obtain data from the App API, and POST is to send data to the App API (for example, to perform insert or update operations).


![mceclip3.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-4.png)


 


'URL' will be the resource you created under the Configuration Builder section of the App in the previous step. Please note that the resource must not be in use (this means, each endpoint will have a unique url, and be either GET or POST).  There cannot be endpoints that share the same url, even if they implement different http methods.


To enforce authentication, check the “Requires Authentication” checkbox  - otherwise, if you want your API to be publicly accessible, leave it unchecked. If checked, you’ll need to include an “Authorization” header. For more information, refer to [Securing API Endpoints with Airkit API Tokens & Permissions](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions).


Under Url Format you can specify the URL path parameters (not to be confused with query parameters) to be sent with the request. This is optional. The parameters need to be set between curly braces and separated by a slash. Example:


 


![mceclip6.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-5.png)


### Configuring the Journey Mapping


Journey Mapping is where to configure the mapping of an API Request to an existing session or conversely, starts a new session. This is also where you can define what validation is needed as a part of the API request by using a Data Flow and can also set a response body and response status. 


In this section, you’ll be able to configure the behavior and the events to occur once a request is received in an endpoint. To achieve this, there are a few different sub-sections at disposal.


![1124925491.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-6.png)


### Sample Payload


This is a sample so you can know how to build the request. After expanding the Sample Payload, hit the Play button to see what that payload would look like.   
  
![mceclip8.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-7.png)  
  



### Validation


Validation offers the ability to validate the HTTP request before continuing on to the Journey Mapping step. This is useful to ensure that the HTTP Request received is valid and has all the proper elements that the API is expecting. For example, if the API Request is expecting an integer, the validation step is where you can pass the payload to a Data Flow and use Airscript to check to see if the request is valid. The output of the Data Flow is then passed to the **connection** namespace, which can be used in the validation step. 


In the example below, we have two path parameters (the same that were specified in the example in in the “Creating an API request handler” section). Since it’s a GET endpoint, there’s no body. If this was a POST endpoint, there could be a body in this payload. You will need to build a Data Flow separately, and set it as the validator step under the **Data Flow** title. This example has a Data Flow set up called "Validation Data Flow", which outputs a concatenated string. 


![mceclip10.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-8.png)


To pass data to the input fields from the API endpoint, use the namespace **payload** to parse the object coming from the Sample Payload. 


![mceclip9.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-9.png)


After running the Data Flow by hitting the 'play' icon, the validation action can be used to validate the outputs of the Data Flow using Airscript. The namespace '**connection**' is the result of the Data Flow configured in the validation step. Also, if the validation returns 'FALSE', then the journey mapping will actually be skipped and will return the response.  


[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/creating-an-api-for-your-airkit-app-v1714-10.png",
        "mceclip0 (2).png",
        575,
        291,
        "#fcfafa"
      ],
      "sizing": "80"
    }
  ]
}
[/block]
**Quick Note**: pay attention to the relevant namespaces here (**payload**, **connection**).


 


### Mapping


This section is where to define what happens after the request has been received and validated, in regards to the journey in particular. You can start a new journey, replace the existing one, abort it or resume it if a match is found (an identifier must be provided).


 **Start Parameters**![startparamatersapi.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-11.png)


Start parameters is where you can pass any type of data that is available from the API request to the journey to **session.start**. Start parameters are only applicable when the **Journey Behavior** is 'Start or Create a new Journey'. 


**Journey Identifier Expression**![jieAPI.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-12.png)


The [journey identifier expression](https://support.airkit.com/docs/journeys) is where to map an identifier on a session from a piece of data out of the payload or connection namespace. For example, if there was a specific ID that came out of the request payload, that ID can then be used as the journey identifier. The identifiers can be of type Text, Journey ID, or Phone. 


**Journey Event Payload** ![jepAPI.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-13.png) Journey event payload is where to pass data from the API endpoint into the API Request **event** namespace.

```javascript Airscript
event
```


### Response


This is what the App API will return after the specified chain of operations are executed. The status and the body are both customizable.  
  
**isValid** will return the outputs from the validation step.   
![mceclip12.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-14.png)


![mceclip13.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-15.png)


NOTE: pay attention to the relevant namespaces here (**payload**, **connection**, **metadata**, **isValid**)


#### Response Headers


This provides the ability to add an [HTTP header in an HTTP response](https://developer.mozilla.org/en-US/docs/Glossary/Response_header). One example that this can be useful is for redirecting to a URL. To do this, set the Response Status to 302 if the response is valid. 


![image__16_.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-16).png)


Then, add an HTTP parameter with the Field Name **"Location"** and the value **metadata.canvas_link.**



[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/creating-an-api-for-your-airkit-app-v1714-17.png",
        "mceclip0 (1)-api.png",
        714,
        348,
        "#fcfbfb"
      ]
    }
  ]
}
[/block]
Publishing and Testing
----------------------


Once finished configuring the App API, the application needs to be published to make the HTTP resource live. To publish, click on the '**Publish**' button in the top right hand corner.  
![mceclip0.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-18).png)


For further information on publishing, refer to [Publishing Your Application.](https://support.airkit.com/docs/publishing-your-application) Once the application is published, the API endpoint is now live and can be receive requests.


To test out the API, there is a feature to simulate HTTP events in the App Preview. This is how to make a request within the App Preview and where to debug and see the different states as well as test out the mapping of the request as well.


When in the studio, go to **App Preview** > **API**. Select **HTTP Request** and enter in the URL of the endpoint and click on **Simulate HTTP Event**. It also provides the capability to pass a request payload as well.  
![mceclip1.png](./assets_v1714/creating-an-api-for-your-airkit-app-v1714-19).png)


Further Reading
---------------


With the API endpoint, this provides an entry point to external systems to communicate to an Airkit Application that can also map to a new journey or existing journeys. For additional related topics, see:


* [Securing API Endpoints with Airkit API Tokens & Permissions](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions)
* [Receiving Inbound HTTP API Requests with your App](https://support.airkit.com/docs/receiving-inbound-http-api-requests-with-your-app)
* [Connecting to External Systems](https://support.airkit.com/docs/connecting-to-external-systems)