Profiles are a mechanism that provide the ability to set up different deployment settings and configurations for an app and can be configured in [Configuration Builder](https://support.airkit.com/docs/configuration-builder). Adding profiles in an application are useful when you want to have multiple deployments and each of those deployments require different configurations. For example, if there was the requirement to have a DEV, QA, and Production deployment with different configurations, you would set up three separate profiles for those deployments.


To create a profile, go to **Configuration Builder** and click on the “**+**” icon. 


![profilesdeployments01.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-0.png)


From here, either create a new profile or create from an existing profile.


![profilesdeployments02.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-1.png)


Once a profile has been created, each of the profiles can have different configurations . For example, if there was a requirement to have different URLS that point to an app for each deployment,  the Web URLs resource can be changed to point to a specific web resource.  


To change profiles, click on the dropdown next to the app name.


![profilesdeployments03.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-2.png)


# Handling multiple deployments for a single application using profiles


Deployments are a way to separate an application into multiple isolated environments. Each deployment will require a unique profile per deployment due to some resources being restricted to a single deployment. To create a new deployment, begin by creating a new locked branch. This will ensure that the branch that is to be deployed will not allow any edits.


After creating an application profile, save the app and go to console.airkit.com and select the application.  Click on **Branches** in the inspector. 


![profilesdeployments04.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-3.png)


Find the current working/unlocked branch and select **Duplicate Branch** in the inspector.


![profilesdeployments05.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-4.png)


Name the branch something unique and select the checkbox stating that the branch is a production branch. The branch name will typically include a version number and/or date  + environment (e.g. QA-1-09/01/2020 , PROD - v1 - 10/10/2020). Then select **Save** to save the branch.


![profilesdeployments06.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-5.png)


Once done saving the branch, go back to Apps. Then select the app and go to **Deployments** from the inspector.


![profilesdeployments07.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-6.png)


Select **+New** to create a new deployment. The deployment name must be unique and it is recommended that the name of the deployment includes the environment name. Select the checkbox to mark the deployment as a production deployment and select the corresponding branch and profile for your deployment. Lastly, click on deploy and now there is an additional deployment of the application!


![profilesdeployments08.png](./assets_v1714/using-profiles-for-deployment-settings-and-configurations-v1714-7.png)


Further Reading
---------------


Profiles are a great way to separate applications into isolated deployments for testing or staging purposes, and provide the capability to create a proper deployment lifecycle of an application. For additional information on publishing an application or related topics, see below:


* [Publishing Your Application](https://support.airkit.com/docs/publishing-your-application)
* [Connecting Your Domain to Airkit](https://support.airkit.com/docs/connecting-your-domain-to-airkit)
* [Connecting Your Twilio Numbers to Airkit](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit)
* [Understanding Profiles](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit)