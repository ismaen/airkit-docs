Overview
--------


The Progress Bar is a web control that can be added to Web Pages. Progress Bars inform users of the completion of a task and the length of a process. 


Adding Progress Bars to Web Pages
---------------------------------


In [Web Builder](https://support.airkit.com/docs/web-builder), go to the first Web Page of your [Web Flow](https://support.airkit.com/docs/web-flows), click on the '+' sign next to it and select the Progress Bar control.


![image3.png](./assets_v1714/creating-a-progress-bar-v1714-0.png)


The Progress Bar will be displayed showing three steps by default.


![image9.png](./assets_v1714/creating-a-progress-bar-v1714-1.png)


In the General tab of the Inspector section, under Control Properties, the following are set by default:


**Value:** the step the current Web Page is in. 


**Steps:** the number of steps this Progress Bar has. 


**ProgressLabels:** the labels shown by default to identify the progress. 


![image4.png](./assets_v1714/creating-a-progress-bar-v1714-2.png)


Setting up the Progress Bar values as a global variable
-------------------------------------------------------


In order to use the Progress Bar across the whole [Journey](https://support.airkit.com/docs/journeys), a Global [Variable](https://support.airkit.com/docs/variable-scopes) needs to be created.


Go to [Journey Builder](https://support.airkit.com/docs/journey-builder) and in the General tab of the Inspector, add a Global Variable of type List of Text.


![image1.png](./assets_v1714/creating-a-progress-bar-v1714-3.png)


Use transparent wording to rename it.


![5PH.png](./assets_v1714/creating-a-progress-bar-v1714-4.png)


Then, from Journey Started in the Actions tab, pick the Set Variable option.


![image5.png](./assets_v1714/creating-a-progress-bar-v1714-5.png)


Enter the recently created Global Variable and, as values, paste here the ones set as ProgressLabels in Web Builder. Additional steps can also be added.


![image2.png](./assets_v1714/creating-a-progress-bar-v1714-6.png)


Also, if you want to provide a more customised experience, you can change the labels of the steps as well:


![image6.png](./assets_v1714/creating-a-progress-bar-v1714-7.png)


Tying the Global Variable to the Progress Bar
---------------------------------------------


From [Web Builder](https://support.airkit.com/docs/web-builder), replace the content on the ProgressLabels control with the Global Variable you created in Journey Builder.


![9.png](./assets_v1714/creating-a-progress-bar-v1714-8.png)


Now, every time you add a Progress Bar control in the application, you can retrieve the same setting using this Global Variable.


Further reading
---------------


To learn more about the properties of the Progress Bar, read [Progress Bar Web Control](https://support.airkit.com/reference/progress-bar-web-control)


To learn more about setting up variables, go  to [Variable Scopes](https://support.airkit.com/docs/variable-scopes)


To check on other Web Controls, go to [Web Controls](https://support.airkit.com/reference/web-controls-overview)