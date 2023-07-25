This article will cover how to connect a domain to Airkit and white label a web url. In order to connect a domain to Airkit, there are a few configuration steps needed.

[block:callout]
{
  "type": "warning",
  "body": "If using a custom domain in an application, whether it is a URL Domain or URL Route, that domain has to be compatible with <https://letsencrypt.org/docs/certificate-compatibility/>."
}
[/block]
Create a CNAME record in your domain provider
---------------------------------------------


Create a CNAME record for the domain with the following values:


usher.woodsidebikes.com -> app.airkit.com.

[block:callout]
{
  "type": "info",
  "body": "The domain must be pointing to app.airkit.com first and propagated before moving on to the next step. Also, based on the realm of the Airkit organization, the url will differ:\n\n\n\n\n**US Realm:** \n```\napp.airkit.com \n```\n**EU Realm:** \n```\napp.airkit.eu \n```\n**APAC Realm:**\n``` \napp.airkit.com.au\n```"
}
[/block]
The below is an example configuration for a domain hosted in Amazon AWS:


<img src="./assets_v1714/connecting-your-domain-to-airkit-v1714-0.png" alt="organizing info" style="max-width: 350px; width:100%;"/>


Creating a URL domain and URL Route
-----------------------------------


To add a URL Domain and a URL Route in Airkit, go to [console.airkit.com](https://console.airkit.com) to add a resource. 


To add a URL domain, under **Resources** click on **+New** and type a unique name to label the domain and select URL Domain in the capabilities drop down.

<img src="./assets_v1714/connecting-your-domain-to-airkit-v1714-1.png" alt="organizing info" style="max-height: 350px; width:100%;"/>


After selecting URL Domain, put in the custom domain name that was created when the CNAME was created. For example: usher.woodsidebikes.com. Airkit will then attempt to retrieve the certificate that was created.  The URL Domain will then be able to be used for canvas links and web launch URLs.


After adding a URL domain, add a URL Route resource. Under the **Resources** tab, Click on **+New** and type a unique name to label the route and select URL Route in the capabilities drop down.


![Screen_Shot_2021-03-03_at_5.49.42_PM__1_.png](./assets_v1714/connecting-your-domain-to-airkit-v1714-2.42%20PM%20(1).png)


Then select the URL domain that was created in the previous step. This will provide the ability to create a custom path on your domain (e.g. usher.woodsidebikes.com/c/order). 


Lastly, add a Custom URL key which give the ability to customize the URL the app will launch at.


Configure the domain in configuration builder
---------------------------------------------


Go to **Configuration Builder** and look for Web Resource. This is where to configure what domain the application is hosted on. Find the URL Route that was created and select that URL Route as the web resource. 


![2021-03-15_17-03-45.png](./assets_v1714/connecting-your-domain-to-airkit-v1714-3.png)


Once published, the application will now use the white-labeled domain!


Further Reading
---------------


White labeling a domain provides a more branded experience for an application. Instead of users seeing app.airkit.com when sent a link, they will see a custom domain. For related information on publishing your application or connecting Twilio numbers, see below:


* [Publishing Your Application](https://support.airkit.com/docs/publishing-your-application)
* [Connecting Your Twilio Numbers to Airkit](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit)
* [Using Profiles for Deployment settings and Configurations](https://support.airkit.com/docs/using-profiles-for-deployment-settings-and-configurations)