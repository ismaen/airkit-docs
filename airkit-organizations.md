### What are Airkit Organizations?


Everything built within Airkit is, at the highest level, sorted into Organizations, or *Orgs* for short. One must have access to an Org in order to access the [console](https://support.airkit.com/docs/console), and all changes made within the Console – all [application resources configured](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app), all [external resources integrated](https://support.airkit.com/docs/setting-up-integrations) – are made at the Organization level. It is also at this level that [user roles](https://support.airkit.com/docs/managing-user-roles) are managed by users with Admin permissions.


Arbitrarily many people can have access to a single Organization, but each user can have only one [role](https://support.airkit.com/docs/managing-user-roles) within it. The role a user has been assigned dictates what within an Organization they will be able to access. For instance, Developers can integrate external resources while Agents cannot.


An individual user might have access to multiple Organizations, in which case they will need to select which Organization they mean to work within before accessing the [Console](https://support.airkit.com/docs/console) after signing in. This individual user might have a different [role](https://support.airkit.com/docs/managing-user-roles) depending on which Organization they access. For instance, someone might be assigned the role of Developer within their company's primary app-building Organization and an Admin role within a separate dev Organization of their own.


When Organizations are provisioned, they can be created in the following regions: US, EU, or Asia Pacific. This can improve latency as well as help with data residency requirements. To provision a new Organization, contact your Airkit representative.


### Importing and exporting Airkit apps to different Organizations


If an app has been built within one Org and needs to be edited in another, it's possible to download an Airkit app as a ZIP file and uploaded that ZIP file to another organization. Apps can be saved as a ZIP file by selecting *Export*from the dropdown menu on the upper right of the [Studio](https://support.airkit.com/docs/studio) when accessing the relevant application:


![2021-09-07_15-47-59__1_.gif](./assets_v1714/airkit-organizations-v1714-0).gif)


This ZIP file can then be uploaded to the new Org by accessing the [Console](https://support.airkit.com/docs/console) of the relevant Organization, clicking the *Create New* button in the upper right corner, and then selecting the relevant ZIP file under *Import App (Optional)*:


![2021-09-07_16-01-02__1_.gif](./assets_v1714/airkit-organizations-v1714-1).gif)


Note that when an app is imported in this way, it will not have access to the same Organization-level resources – such as [external integrations](https://support.airkit.com/docs/setting-up-integrations) or [Twilio phone numbers](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit) – that it used to. This means that the application will likely require changes to be made in [Configuration Builder](https://support.airkit.com/docs/configuration-builder) before being published in its new Organization. Depending on the needs of the application, [API integrations and other systems](https://support.airkit.com/docs/your-apis-and-systems-connect-to-airkit) might also need to be configured at the Organization level.