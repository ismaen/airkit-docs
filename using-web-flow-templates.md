Overview
--------


[Web Flow](https://support.airkit.com/docs/web-flows) templates provide a simple way to start building an application with commonly used actions. Web Flow templates are pre-configured but they can be further tailored for a customized experience.  Within a Journey, there can be multiple Web Flows, each built with a specific purpose, and they can be connected among each other. 

Creating a Web Flow from a template
-----------------------------------


There are two ways to create Web Flows from a template:


1. From the Web Builder: Web Flow templates can be added by clicking on the ‘**+**’ icon next to Web.  
![addwebflowtemplate.png](./assets_v1714/using-web-flow-templates-v1714-0.png)
2. From the Journey Builder: Web Flow templates can be added by clicking on the ‘**+**’ icon in an Event and selecting Navigate to Web Flow.


![fromjourney.png](./assets_v1714/using-web-flow-templates-v1714-1.png)


A blank canvas will be displayed to click on the ‘**+**’  icon and add a new Web Flow template.


![fromjourney2.png](./assets_v1714/using-web-flow-templates-v1714-2.png)


Combining Web Flows
-------------------


In this example, two Web Flow templates were added to the application: “Capture Customer Info” and “CSAT”, each with their pre-configured fields and actions. In addition, the “Capture Customer Info” Web Flow includes the button “Next” which runs the “Contact Info Captured” Event. This Event allows the two Web Flows to be combined so that users can go from one to the other as they move forward in the Journey.


![connect1.png](./assets_v1714/using-web-flow-templates-v1714-3.png)


To do so, in the Journey Builder, a [Navigate to Web Flow](https://support.airkit.com/reference/navigate-to-web-flow-action) action must be added to the “Contact Info Captured” Event.


![connect2.png](./assets_v1714/using-web-flow-templates-v1714-4.png)


Finally, select which Web Flow to navigate to when the Event is run.


 


![connect3.png](./assets_v1714/using-web-flow-templates-v1714-5.png)


Passing Data from One Web Flow to Another
-----------------------------------------


Data entered in the Input fields can be passed from one Web Flow to the other. In this example, to provide a more customized experience, the name the user entered in the Input field of the Capture Customer Info Web Flow will be used in the CSAT Web Flow. To do so, in Web Builder add a “first_name” Variable of type Text at the CSAT Web Flow level.


![1.variableRED.png](./assets_v1714/using-web-flow-templates-v1714-6.png)


Then, go to the Web Page that will include the user’s name. Select the corresponding Label and in the General tab add the Variable in the Text field:



```javascript Airscript
“Hello, {{first_name}}”
```

 Make sure you enter the Variable in the Expression box that gets displayed when clicking on the arrow.


![2.label.png](./assets_v1714/using-web-flow-templates-v1714-7.png)


Finally, go to Journey Builder and click on the Contact Info Captured Event. It already shows the Navigate to CSAT action set up above. Now in Input, add the first_name Variable.


![3.eventRED.png](./assets_v1714/using-web-flow-templates-v1714-8.png)


This way, the data entered as name in the first Web Flow will be passed onto the CSAT Web Flow. When Previewed it looks like this:


![4.preview.png](./assets_v1714/using-web-flow-templates-v1714-9.png)