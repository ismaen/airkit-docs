An App API can be configured to require authentication or to be publicly available. This article will cover how to secure an App API endpoint using API Tokens. 


Creating a Token
----------------


If the App API requires authentication, a token must be created. To create a token, go to [console.airkit.com](http://console.airkit.com) and click on **API** in the left hand navigation. Then click on **Tokens** > '**+New**' > enter in a name for the token. You can also configure user variables and IP addresses for additional layers of permissions.


![2021-03-30_15-40-53__2_.gif](./assets_v1714/securing-api-endpoints-with-airkit-api-tokens-and-permissions-v1714-0).gif)


Then click **Create**, which will generate a token.

[block:callout]
{
  "type": "warning",
  "title": "",
  "body": "Make sure to safely store the generated token at that moment since it will not be retrievable afterwards."
}
[/block]



Configuring the API to require Authentication
---------------------------------------------


To configure the API to require Authentication, go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and select the API created under '**Web Links**'.  
  
![mceclip1.png](./assets_v1714/securing-api-endpoints-with-airkit-api-tokens-and-permissions-v1714-1.png)  
  
Then Click on the checkbox under Requires Authentication. This will enforce the API to have a Bearer token with the API Request.   
![mceclip3.png](./assets_v1714/securing-api-endpoints-with-airkit-api-tokens-and-permissions-v1714-2.png)


To add an API Key Group, which is used to give API access to particular users within an organization, go to Configuration Builder, scroll down to **API Key Filtering**, add an **API Key Group**. Then select the Token name created previously.


![mceclip4.png](./assets_v1714/securing-api-endpoints-with-airkit-api-tokens-and-permissions-v1714-3.png)


Once the API Key group is configured, then it can be configured to the API.


![mceclip5.png](./assets_v1714/securing-api-endpoints-with-airkit-api-tokens-and-permissions-v1714-4.png)


Testing the App API
-------------------


To test an API that requires authentication, the following header must be set:  
"**Authorization: Bearer <token>**" where **<token>** is replaced with the token generated in the "Creating a Token" section. Below is a screenshot of testing the API from Postman. 


![secureendpoint.png](./assets_v1714/securing-api-endpoints-with-airkit-api-tokens-and-permissions-v1714-5.png)


 


Further Reading
---------------


* [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app)
* [Receiving Inbound HTTP API Requests with your App](https://support.airkit.com/docs/receiving-inbound-http-api-requests-with-your-app)
* [Connecting to External Systems](https://support.airkit.com/docs/connecting-to-external-systems)