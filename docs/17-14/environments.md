Environments provide the capability to separate [integrations](https://support.airkit.com/docs/setting-up-integrations), [resources](https://support.airkit.com/docs/adding-and-modifying-resources), [APIs](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app), and [tokens](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions) within an organization. Environments serve as a container to organize these resources and allow builders to silo them based off of their use case. Every organization comes pre-provisioned with three default environments: DEV, STAGING, and PROD. These environments can then be used to assign resources to their respective environment, which can then be tied to a specific application using [profiles](https://support.airkit.com/docs/using-profiles-for-deployment-settings-and-configurations).


![mceclip4.png](./assets_v1714/environments-v1714-0.png)



Assigning a resource to an environment
--------------------------------------


When creating an integration, resource, or API in the [console](https://support.airkit.com/docs/console), builders have the option to select the environment in which it will be accessible in.  For example, when adding an integration, there is the option to select the environment that the integration will be created in.


<img src="./assets_v1714/environments-v1714-1.png" alt="organizing info" style="max-width: 250px; width:100%"/>

By creating the integration in the DEV Environment, the integration will only appear as a selectable option if the DEV environment is selected in [Configuration Builder](https://support.airkit.com/docs/configuration-builder).  To select the environment, go to **Configuration Builder** > **Global** and select DEV in the Environment dropdown. 


![mceclip2.png](./assets_v1714/environments-v1714-2.png)


Then when adding the integration, the integration should be accessible in the list of options.   

<img src="./assets_v1714/environments-v1714-3.png" alt="organizing info" style="max-width: 400px; width:100%"/>

Environments and Profiles
-------------------------


It is considered best practice to have your profiles and environments aligned. For example, the development profile should have the DEV environment configured, QA profile with the STAGING environment, and the Production profile with the PROD environment. By default, the environments are tied to their corresponding profiles, but you do have the option to change them. If changed, the resources will need to be reselected after switching.