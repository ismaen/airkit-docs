Overview
--------


[Data Flow](https://support.airkit.com/docs/data-flows) templates provide a simple way to connect data in an application with commonly used actions. 


Data Flow templates are pre-configured but they need to be further tailored for a customized experience.


Within a Journey, there can be multiple Data Flows, each built with a specific purpose, and they can be triggered from different parts of the application.


Submitting a CSAT score into Airdata
------------------------------------


In this example, a Save CSAT Data Flow has been created to store the application's feedback and score users submit through a Web Flow.


### Creating a Data Flow from a template


From the [Connection Builder](https://support.airkit.com/docs/connection-builder), Data Flow templates can be added by clicking on the ‘+’ sign next to Data Flow. This example will use the "**AirData Insert Record**" Data Flow. Data Flow templates are created with some pre-configured information. However, they need to be adjusted to the application’s use case.


![dataflownew.png](./assets_v1714/using-data-flow-templates-v1714-0.png)


It is also good practice to rename Data Flows to easily identify them across the application.


In this example, the Data Flow will save information from the inputs of the "CSAT" Web Flow Template to the an [app object](https://support.airkit.com/docs/airdata-app-objects) called "CSAT".


![mceclip0.png](./assets_v1714/using-data-flow-templates-v1714-1.png)


When a Data Flow is called, the operation steps are executed sequentially starting at the top and working down the Stage. 


At Start, create an input for this Data Flow with the type CSAT. This is accessible by clicking on the '+' icon and going to **objects** > **CSAT**


![INPUT.png](./assets_v1714/using-data-flow-templates-v1714-2.png)


Then, in the AirData Request data operation, select the CSAT App object, the Payload Type is INSERT and the object to insert is also CSAT.


![OBJECT.png](./assets_v1714/using-data-flow-templates-v1714-3.png)


### Connecting Data Flows to Controls


Data Flows are initiated by some other part of the application. 


Following the example above, in the [Web Builder](https://support.airkit.com/docs/web-builder) of this app, there is a CSAT Web Flow requesting users to score the app and submit feedback. Once they select a score and leave their comments, they click on a “Submit” button.


In order to store that information in the Save CSAT Data Flow, the following steps should be followed: 


1. Click the “Submit” button in the CSAT Web Flow![dataflowbutton.png](./assets_v1714/using-data-flow-templates-v1714-4.png)
2. Click the ‘+’ sign under Actions and select a Data Action![dataflowbuttonandplus.png](./assets_v1714/using-data-flow-templates-v1714-5.png)
3. Select the previously created Save CSAT Data Flow![webflowselectdata.png](./assets_v1714/using-data-flow-templates-v1714-6.png)
4. Add the corresponding inputs to the Data Flow


![inputwebflow.png](./assets_v1714/using-data-flow-templates-v1714-7.png)



```javascript Airscript
{"score": CSAT,"feedback": feedback}
```

As a result, when the customer submits their score and feedback, the values will be saved in the CSAT object through the Save CSAT Data Flow.


Further Reading
---------------


* [Introduction to Data Flows](https://support.airkit.com/docs/data-flows)
* [Connection Builder](https://support.airkit.com/docs/connection-builder)
* [Web Builder](https://support.airkit.com/docs/web-builder)