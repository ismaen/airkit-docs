Setting up Authenticated Integrations
-------------------------------------


### Standard Integrations


Applications have the ability to natively integrate with many popular services, including Twilio, Zendesk, Salesforce, and more. When setting up an integration, the services can be displayed and managed right from your application. For example, when [setting up a Salesforce integration](https://support.airkit.com/docs/create-a-salesforce-lead), Airkit will bring in all of the tables that are associated with a Salesforce account and can then leverage the built in operations such as Create Record, Delete Record, Update Record, Find Records or Query Records.


### Creating a Custom Integration


Custom integrations can be used to connect to external data sources that are not a part of Airkit's standard integrations. Any one of these standard authentication methods can be used for your API. 

For a more detailed breakdown of what is required to create an integration using these authentication methods, see [Custom Integrations](ref:custom-integrations),


* [OAuth 2.0](https://support.airkit.com/v17.15/reference/custom-integrations#oauth-20)
* [API Token](https://support.airkit.com/v17.15/reference/custom-integrations#api-token)
* [HTTP Basic Auth](https://support.airkit.com/v17.15/reference/custom-integrations#http-basic-auth)
* [Custom Token](https://support.airkit.com/v17.15/reference/custom-integrations#custom-token)
* [SFTP](https://support.airkit.com/v17.15/reference/custom-integrations#sftp)

### Using OAuth 2.0 to integrate Twitter


This example demonstrates how to create a custom authenticated integration with the Twitter API that uses OAuth 2.0 and connect it to an Airkit application. 


**Note**: When setting up an OAuth 2.0 integration in Airkit, a refresh token is expected, and the system/endpoint must be configured accordingly. Some systems will automatically account for this and some systems may not. 


**Prerequisites**


* [Twitter developer account](https://developer.twitter.com/content/developer-twitter/en/docs/basics/developer-portal/overview)
* A [Twitter App](https://developer.twitter.com/content/developer-twitter/en/docs/basics/developer-portal/guides/apps) with a developer account


**Setting up your custom integration**


1. Sign in to [console.airkit.com](https://console.airkit.com) and select **Integrations** and then **Custom Integrations.**This is where to manage the integrations associated with an organization.  
![cusromintsmall.png](./assets_v1714/setting-up-integrations-v1714-0.png)
2. Then click on **Create new** to add a new Custom Integration. Enter the name of the service  and a unique key. This key is a global unique identifier associated with your custom integration. Then select OAuth 2.0 for the Authentication Type. This will then expand the fields that are required to create the integration.  
![createnew1.png](./assets_v1714/setting-up-integrations-v1714-1.png)
3. For the [Twitter API](https://developer.twitter.com/en/docs), provide the following for the configuration fields:  

	* **Authorization Grant Type:** choose 'Client Credentials'
	* **Access Token Endpoint:** enter <https://api.twitter.com/oauth2/token>
	* **Access Token Verb:** choose 'POST'
	* **Authorization Endpoint:** enter <https://api.twitter.com/oauth2/token>  
	![createnew2.png](./assets_v1714/setting-up-integrations-v1714-2.png)
	* **OAuth Scope:** enter 'read'
	* **Client ID:** enter your API key that was generated from the Twitter App
	* **Client Secret:** enter in your API Secret generated from the Twitter App
	* **Token Parameter Type**: choose 'Header'
	* **Token Parameter name**: enter 'Authorization'
	* **Token Parameter Value Template**: enter 'Bearer {token}'  
	![createnew3.png](./assets_v1714/setting-up-integrations-v1714-3.png)
4. Click on **Create** to finish creating the custom integration


**Connecting the custom integration to Airkit**


After setting up the custom integration, you need to connect the integration to Airkit. This will surface the integration to your application and make it usable in the app. 


1. In the Airkit Console, go to **Integrations** and then **Connected Accounts.  
![connectedaccountsmall.png](./assets_v1714/setting-up-integrations-v1714-4.png)**
2. Click on **Create new** and give the credential a name and choose the Twitter integration in the drop down menu. Then click on **Create**, which then enables you to connect Twitter to your Airkit App!  
  
![connectedaccountTwitter.png](./assets_v1714/setting-up-integrations-v1714-5.png)


### Using an API Token to integrate with GIPHY


This example demonstrates how to create a custom integration with the [GIPHY API](https://developers.giphy.com/docs/sdk) that uses an API Token and connect it to an application.


**Prerequisites**


* [GIPHY Developer Account](https://developers.giphy.com/)
* GIPHY App with associated API Key


**Setting up your custom integration**


1. Sign in to [console.airkit.com](https://console.airkit.com) and select **Integrations** and then **Custom Integrations.**This is where to manage the integrations associated within organization.  
![cusromintsmall.png](./assets_v1714/setting-up-integrations-v1714-0.png)
2. Then click on **Create new** to add the new Custom Integration. Enter the name of the service and a unique key. This key is a global unique identifier associated with your custom integration. Then select API Token for the Authentication Type. This will then expand the fields that are required to create the integration.  
  
![giphy1.png](./assets_v1714/setting-up-integrations-v1714-7.png)
3. For the GIPHY API, provide the following for the configuration fields:
	* **Token Paramater Type**: choose 'URL Parameter'
	* **Token Parameter Name:** enter 'api_key'
	* **Token Parameter Value Template:** enter '{token}' ![giphy2.png](./assets_v1714/setting-up-integrations-v1714-8.png)
4. Click on **Create** to finish creating the custom integration


**Connecting your custom integration to Airkit**


After setting up the custom integration, you need to connect the integration to Airkit. This will surface the integration to your application and make it usable in the app. 


1. In the Airkit Console, go to **Integrations** and then **Credentials.  
![connectedaccountsmall.png](./assets_v1714/setting-up-integrations-v1714-4.png)**
2. Click on **Create new** and give the credential a name and choose the GIPHY integration in the drop down menu.   
![giphy3.png](./assets_v1714/setting-up-integrations-v1714-10.png)
3. Then provide your API Token from your GIPHY app and click on **Create** to create an integration from GIPHY to Airkit.


![GIPHY4.png](./assets_v1714/setting-up-integrations-v1714-11.png)


Using Integrations in an App
----------------------------


Now that the integrations is added, they can now be used in an application. Integrations can be used to call API endpoints directly from [Connection Builder](https://support.airkit.com/docs/connection-builder) using the HTTP Operation. 


### Adding an integration into an Airkit App


To use the integration, it needs to be added to your app from [Configuration Builder](https://support.airkit.com/docs/configuration-builder). 


1. In the Airkit studio, go to **Configuration Builder** and scroll down to Integrations. Then click on **+New** > **Adapters** and select the custom integration that was created in the console.  
![configbuilder.png](./assets_v1714/setting-up-integrations-v1714-12.png)
2. Then select the credential that is associated with your custom integration and Save your app. This will enable your app to leverage your integration in the HTTP Operation in Connection Builder.  
![configbuilder2.png](./assets_v1714/setting-up-integrations-v1714-13.png)


### Understanding Profiles and Integrations


Oftentimes when building out an application, there's the need to have separate environments such as DEV, QA, and Production environments. For example, you can set up a DEV environment with a dev instance of a custom integration, and be able to test and debug an application without needing to touch production data. To configure this, you need to [set up different profiles](https://support.airkit.com/docs/publishing-your-application) within your application, and each profile would have different configuration settings. 


Next steps
----------


Now with the integrations set up, an application can then be used for inbound requests to [query and manipulate data on external systems](https://support.airkit.com/docs/querying-and-manipulating-data-from-external-systems). Integrations can also be used for outbound requests to [push data from Airkit to external systems](https://support.airkit.com/docs/passing-data-from-external-systems) as well.