Airkit embeds provide yet another way to make your apps available to your customer. Embedding helps provide your apps directly inside your existing web pages. Embeds have a variety of uses. The lead capture form on our [home page](https://www.airkit.com) is an embedded Airkit application. A simple application that collects information about a customer and loads it into our database. The example apps on our website are also Embeds. They are iFrames where an airkit application is loaded. Embeds can exist on one web page or across an entire site. 


This article will cover the basics of creating a simple embed for your app. This article requires a published app and will use a simple Lead Capture example app.


Creating the Embed in Console
-----------------------------


Go to [Console](https://support.airkit.com/docs/console), select the Resources tab. Select the Embeds section. Click the New Button. Give the Embed a name. Embeds only work with [deployed apps](https://support.airkit.com/docs/publishing-your-application). Select a deployed app from the App dropdown menu. Select the deployment from the Deployment dropdown.



<img src="./assets_v1714/embedding-an-airkit-experience-on-your-website-v1714-0.png" alt="organizing info" style="max-width: 250px; width:100%;"/>

In order to display the app on a page, a target hostname is required. For the purposes of the example, include three: **http://**, **https://**, and **file://**. This will allow for testing locally and the embed to be served on both a http and https provided resource.  


Select the checkboxes for "Use Launcher", "Show Launcher on Load", and "Show Frame on load." This will display both the icon and the app when the page loads. In the styles box, scroll down to **buttonImage**, and insert a valid image URL for the "src" value. Click Create.


![LeadCapture-Embeds-CreatedEmbed.png](./assets_v1714/embedding-an-airkit-experience-on-your-website-v1714-1.png)


Click on the icon under Embed script to copy the HTML to display the embed. Paste the copied code into a web page. Open the page in a browser. The embed will be displayed on the first rendering of the page.


<img src="./assets_v1714/embedding-an-airkit-experience-on-your-website-v1714-2.gif" alt="organizing info" style="max-width: 350px; width:100%;"/>
The embed on this page is launching a simple lead capture. When the embed launches it creates a new session for the user. Each time the page is loaded the web launch trigger is hit and the app starts a session.


To delay the display of the lead capture to allow the user to see the page first, set the value of "Show Frame on Load After Duration" to "5000." This is in milliseconds so this means the frame will now be rendered in 5 seconds. Click Update. Go back to the resource where the embed is located and refresh.


Show Frame on Load After Duration is just one of many configurable properties on Embeds. Check out [Airkit Embeds: AirClient Configurable Properties](https://support.airkit.com/docs/airclient-configurable-properties) for a full list of the properties that can be configured on an Embed.