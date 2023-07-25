Publishing your app for the first time
--------------------------------------


When ready to deploy an application and make it live for end users, the next step is to publish the app. Publishing an app connects the resources configured in [Configuration Builder](https://support.airkit.com/docs/configuration-builder) to the app, making it live and accessible to the outside world. Publishing an app also locks down a version of the app, so additional changes to the app won’t affect the current users.


Before publishing an app, all the necessary resources needs to be configured and bound to the app. First, determine what channels the app is going to be communicating on. This will be dependent on whether any chat bots or voice bots are configured in the application. After determining what channels the application will be available and communicate on, go over to the **Configuration Builder** and bind those specific channels to specific resources. 


To create resources in your organization, see [Adding and Modifying Resources](https://support.airkit.com/docs/adding-and-modifying-resources).


### Configuring your application resources


After adding the resources that in the application, they will need to be configured in Configuration Builder. There are a few places where resources need to be configured depending on what channels are being used in the application.


 


**Voice Bot**


![Screen_Shot_2021-02-22_at_4.33.35_PM.png](./assets_v1714/publishing-your-application-v1714-0.png)  
  



If the application uses a voice bot, a voice resource will need to be configured in the application before publishing. 


 


**SMS Bot**


![mceclip0.png](./assets_v1714/publishing-your-application-v1714-1.png)


If the application uses a chat bot, a SMS resource will need to be configured in the application before publishing. 


 


**Canvas Links**


![mceclip1.png](./assets_v1714/publishing-your-application-v1714-2.png)  
  



Configure canvas links before publishing to create journey specific links. Selecting “Default URLs” will use app.airkit.com. To white label the URL, see [Connecting Your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit).


 


**Web URLs**


![mceclip2.png](./assets_v1714/publishing-your-application-v1714-3.png)


To configure the resource to use as the launch url/launch trigger, add a web resource for the Web URL before you publish. Selecting “Default URLs” will use app.airkit.com.


**Portal Link  
![mceclip3.png](./assets_v1714/publishing-your-application-v1714-4.png)**


If the application has a portal associated with it, the Portal Link will need to be configured before publishing.


Publishing the App
------------------


Once the resources are configured, click on the Publish button at the top right corner of the screen. 


  
![mceclip1.png](./assets_v1714/publishing-your-application-v1714-5).png)  



 


This will open up a publishing modal which will provide the option to change the [configuration profile](https://support.airkit.com/docs/using-profiles-for-deployment-settings-and-configurations) as well as the resources that will also be published. This modal also provides the options to send error notifications to various channels and under various circumstances. For a deeper dive into implementing app error notifications, check out [Configuring App Error Notifications to Slack](https://support.airkit.com/docs/configuring-app-error-notifications-to-slack).


![Screen_Shot_2021-10-19_at_1.49.43_PM.png](./assets_v1714/publishing-your-application-v1714-6.png)


After publishing the application, Airkit will provide a URL where the application is currently hosted. Publishing the application will also make any APIs or resources that are associated public as well. 


Further Reading
---------------


Publishing an application is how to make an application live and accessible to end users. Any saved changes that are made after publishing are not reflected to end users until the application is republished. For further information, such as white labeling a web url, or using profiles to set up multiple environments see the articles below. 


* [Connecting Your Twilio Numbers to Airkit](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit)
* [Connecting Your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit)
* [Using Profiles for Deployment settings and Configurations](https://support.airkit.com/docs/using-profiles-for-deployment-settings-and-configurations)