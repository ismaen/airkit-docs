The Configuration Builder dictates the paths through which your Airkit apps interact with external sources. This allows you to do everything from configure the URLs that launch your web apps to authenticate external systems of record. The Configuration Builder is also where can create different Profiles with access to different resources and app-level configurations, which can be used when deploying the app under different circumstances. Most commonly, different Profiles will be made to ensure that an app deployed for testing and development purposes cannot interact with the outside world in the same way as when deployed to production.


# Profiles


A Profile is a group of configuration settings. When working in the Configuration Builder, you are making changes to a Profile, and you can select which Profile you are working with by selecting a Profile from the drop-down menu at the top of the Configuration Builder. By default, every Airkit app comes out of the box with three Profiles: **Dev**, **QA**, and **Production**:

<img src="./assets_v1714/configuration-builder-v1714-0.gif" alt="organizing info" style="max-width: 400px; width:100%"/>


Whenever you deploy your app, you'll have the option of using any of the available Profiles. This allows different deployments of your app to incorporate themselves differently with the outside world. For instance, depending on your needs, different deployments of you application might send text messages from different phone numbers, be accessed through different URLs, or integrate with different systems of record. Each of your Airkit apps might have any number of different Profiles, and you can add new Profiles by clicking on the '+' icon on the upper right of the Configuration Builder.

<img src="./assets_v1714/configuration-builder-v1714-1.gif" alt="organizing info" style="max-width: 400px; width:100%"/>

When previewing your application, your emulated app will behave as though using whatever Profile is currently selected in the Configuration Builder.


# Global Settings


Every Profile has its own global settings, which define fundamental information regarding how your application will behave.

<img src="./assets_v1714/configuration-builder-v1714-2.png" alt="organizing info" style="max-width: 400px; width:100%"/>

* **Locale** - Dictates the default language and timezone of your application. Changes to either can be made by selecting a new language or timezone from the dropdown menus.
* **Session Expiration Time** - Defines how long a [Journey](https://support.airkit.com/docs/journeys) through the app will last before expiring. The maximum session duration is 90 days.  
* **App Authentication Type** - Designates the authentication type that you would designate your app if you were creating an authenticated app experience.
* **Delete Profile** - Deletes the profile you are working within.


# Voice Bot


This section is used to define how your app will make and handle phone calls when deployed. You will need to add the relevant resources to your Organization via the [Console](doc:console) in order to have access to them in the Configuration Builder. For more on how to add phone resources to your Organization, check out [Connecting your Twilio Numbers to Airkit](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit).

<img src="./assets_v1714/configuration-builder-v1714-3.png" alt="organizing info" style="max-width: 400px; width:100%"/>

* **Voice Resource** - The voice resource (selected from the the voice resources available within your organization) that the application will take and send calls from.
* **Voice Locked Behavior** - How the application behaves when the voice resource cannot be reached.
* **Voice Bot Behavior When Launched** - How launching a Voice Bot impacts a user's [Journey](https://support.airkit.com/docs/journeys).


# Chat Bot


This section is used to define how your app will make and handle text messages when deployed. You will need to add the relevant resources to your Organization via the [Console](doc:console) in order to have access to them in the Configuration Builder. The dropdown menu under **SMS Resource** will allow you to select from all relevant resources within your organization:

<img src="./assets_v1714/configuration-builder-v1714-4.png" alt="organizing info" style="max-width: 400px; width:100%"/>


For more on how to add SMS resources to your Organization, check out [Connecting your Twilio Numbers to Airkit](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit).


# Integrations


Integrations represent connections to external systems of record. Once your Airkit app is integrated with an external system of record, data can flow easily between them.


Integrations are created through adapters, and you define which Data Source your app uses for each configuration. This can be useful when using different sources of record for production or development.


You will need to add the relevant resources to your Organization via the [Console](doc:console) in order to have access to them in the Configuration Builder. When adding a new integration (by selecting the '+ New' icon on the bottom left), you will only be able to select options from relevant resources within your Organization:


 


![2021-06-29_13-39-44__1_.gif](./assets_v1714/configuration-builder-v1714-5).gif)


For more on how to integrate external systems of record to your Organization, check out [Connecting Airkit to Your Systems](https://support.airkit.com/docs/setting-up-integrations).


# Email


This section is used to configure email addresses and email domain addresses that can be used to send emails from within Airkit: 

<img src="./assets_v1714/configuration-builder-v1714-6.gif" alt="organizing info" style="max-width: 400px; width:100%"/>


You will need to add the relevant resources to your Organization via the [Console](doc:console)  in order to have access to them in the Configuration Builder. For more check out [Setting up email domains and addresses in Console](https://support.airkit.com/docs/sending-email-from-airkit) and [Configuring a Domain for Sending Email](https://support.airkit.com/docs/configuring-a-domain-for-sending-email). 


# API Key Filtering


Airkit apps can be associated with their own APIs, to use when you need to interact with your apps or the data within them outside of Airkit. The *API Key Filtering* section is used to permission your App API based on API Keys:

<img src="./assets_v1714/configuration-builder-v1714-7.gif" alt="organizing info" style="max-width: 400px; width:100%"/>

You will need to have a relevant web resource to your Organization via the [Console](doc:console) in order to configure your API in this way. For more on how to set this up, see [Creating an API for your Airkit App](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app).


# Canvas Links

This section is used to define the web resources that your app will use when deployed. (By default, this app resource is app.airkit.com.) This differs from the web resources defined under **Web URLs **because these links are associated with individual user [Journeys](https://support.airkit.com/docs/journeys-The-Journey-Model); going a canvas link allows a user to continue an existing Journey, rather than start a new one.


You will need to add the relevant URL resource to your Organization via the [Console](doc:console) in order to have access to it in the Configuration Builder. For more on how to add these resources to your organization, check out [Connecting Your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit).

<img src="./assets_v1714/configuration-builder-v1714-8.png" alt="organizing info" style="max-width: 400px; width:100%"/>


* **Web Resource** - The domain that will be associated with the web component of your app.
* **Canvas Link Length** - The length the path of URL that links to a particular user's [Journey](https://support.airkit.com/docs/journeys-The-Journey-Model); this will be automatically generated so that it is unique for each Journey.
* **Expired Session HTML** - Defines what a users sees should they try to open a link that leads to an expired Journey.


### Web URLs


The web URL is the URL that will launch your app's web experience. This differs from the web resources defined under [Canvas Links](#h_01F9CRYV3PD6PPPCA4HYYSBMZ7), because the URL defined here will start a new [Journey](https://support.airkit.com/docs/journeys-The-Journey-Model) through the application, rather than direct the user to an existing one.


You will need to add the relevant URL resource to your Organization via the [Console](doc:console) in order to have access to it in the Configuration Builder. For more on how to add these resources to your Organization, check out [Connecting Your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit).


![2021-06-29_13-48-51__1_.gif](./assets_v1714/configuration-builder-v1714-9).gif)


* **Name** - The name to associate with this launch URL.
* **SAML Auth** - How users will be authenticated, if necessary.
* **Web Resource** - The domain to associate with launching a web component of your application.


### Portal Link


This section is used to configure the URL leading to any [Portals](https://support.airkit.com/docs/capabilities-of-portals) associated with your application. You will need to add the relevant URL resource to your Organization via the [Console](doc:console) in order to have access to it in the Configuration Builder. For more on how to add these resources to your Organization, check out [Connecting Your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit).


![2021-06-29_13-52-59.png](./assets_v1714/configuration-builder-v1714-10.png)


### Data Store


This section is used to select the primary [Datastore](https://support.airkit.com/docs/datastores) associated with your current Profile. This is where data will be stored to and queried from once your app is deployed.


![2021-06-29_13-53-28.png](./assets_v1714/configuration-builder-v1714-11.png)


### Analytics


This section is used to install third-party data analytics providers such as [Heap](https://support.airkit.com/docs/setting-up-analytics-with-heap) or [Google Tags](https://support.airkit.com/docs/setting-up-analytics-with-google-tag-manager). 


![2021-12-06_11-24-42.png](./assets_v1714/configuration-builder-v1714-12.png)