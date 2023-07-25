When building an application with [multiple profiles and deployments](https://support.airkit.com/docs/using-profiles-for-deployment-settings-and-configurations), oftentimes they require different configuration settings or inputs based on the deployment. To help with this, variables are capable of being promoted to an App Setting variable, which allows variables to be configured and initialized at the profile level.  For example, if there are multiple deployments such as QA or PROD, App Setting variables can be used to initialize different IDs/URLs based on those deployments so the application can have different parameters set at the profile level. The benefit of using App Setting variables is that the variables are all surfaced in Configuration Builder, which makes managing the variables a lot easier across different deployments.


How to promote a variable to an app setting
-------------------------------------------


Any type of variables can be promoted to App Setting variables, whether they are on Web Pages, [Web Flows](https://support.airkit.com/docs/web-flows), or [Global Variables](https://support.airkit.com/docs/standard-journey-data). To promote a variable to an App Setting variable right-click on the variable in the inspector. A dropdown will appear and provide the option to '**Convert to Setting**'. 


<img src="./assets_v1714/promoting-variables-to-an-app-setting-v1714-0.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

After converting the variable to an App Setting Variable, the variable can be accessed in **Configuration Builder**. To access the App Setting variable, go to Configuration variable and scroll down to App Settings. This is where the variable can be initialized for each profile. The value also accepts [Airscript](https://support.airkit.com/docs/airscript-quick-start) as well.


![mceclip1.png](./assets_v1714/promoting-variables-to-an-app-setting-v1714-1.png)


Using the App Setting Variable
------------------------------


The App Setting variable can be accessed in Web Builder by using the '**profile**' namespace. For example, to access the App Setting variable in the previous example, use:



```javascript Airscript
profile.id
```

Further Reading
---------------


App Setting variables are great tools for creating additional configuration settings within an application. For more information on variables, see:


* [Standard Journey Data](https://support.airkit.com/docs/standard-journey-data)
* [Variable Scopes](https://support.airkit.com/docs/variable-scopes)
* [The Set Variable Action](https://support.airkit.com/reference/the-set-variable-action)