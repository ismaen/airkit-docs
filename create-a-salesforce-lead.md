Airkit is designed to work with many different platforms, providing a better front end for your digital experiences. In this guide we walk through creating a lead in Salesforce. We start with configuring your Organization for working with your Salesforce account and then move creating a connection to create a lead.


Setting up your connection to Salesforce
----------------------------------------


Setting up your Airkit Organization to talk to your Salesforce Organization is the first step. Go to the console and click on the **Integrations** tab on the left. With **Credentials** selected (it’s selected by default when you click integrations), click **New** on the right. From the Integration list select **Salesforce**. Name your Credential something you will remember like your Salesforce Org Name. ![create-sf-lead1.png](./assets_v1714/create-a-salesforce-lead-v1714-0.png)


You will be presented with the Salesforce Login Page. Log in with your Salesforce Credentials. Once you are connected you will see an additional item on your **Credentials** page for your new connection.


Now we need to connect this to your application. Click on **Apps** on the left hand side, select your app, and click the **Edit In Studio** button in the **Inspector**. From there select **Configuration Builder** from the Builder Bar. Scroll down to the **Integrations** section and click the new button. Under **Adapters** you will see **Salesforce** option to select. ![create-sf-lead2.png](./assets_v1714/create-a-salesforce-lead-v1714-1.png)


In the **Datasource** section of the new integration, select the Salesforce credential you just created. **Save** your app.


Creating the Connection
-----------------------


Now that your app is connected to your Salesforce account, the next step is to create a connection to create a Lead object. Select **Connection Builder** from the **Builder Bar** on the right hand side. Add a new **Data Operation**. ![create-sf-lead3.png](./assets_v1714/create-a-salesforce-lead-v1714-2.png)


Double click on the connection name in the **Tree** and rename the connection to “SF - Create a Lead”. Change the type of the first **Data Operation Step** to **Salesforce**. Make sure the datasource you created is selected for the Datasource. ![create-sf-lead4.png](./assets_v1714/create-a-salesforce-lead-v1714-3.png)


Next select **Create Record** operation and for **Object Type** look for **Lead**. Notice that the **Object Body** is already set up with the required fields to create a **Lead** object in your Salesforce instance. Fill them out and click the play button at the top of the **Data Operation Step**. ![create-sf-lead5.png](./assets_v1714/create-a-salesforce-lead-v1714-4.png)


If you were successful you will see run results that look something like this:



```javascript Airscript
{
  "success": true,
  "result": {
    "id": "00Q4x000001l9oKEAQ",
    "success": true,
    "errors": []
  },
  "errorMessage": null
}

```

Adding other properties to your Lead
------------------------------------


Selecting the **Lead** option from the dropdown enters fields for creating the required fields for your **Lead** object in salesforce. You can select the plus button below the required items to add any additional fields required by your lead object. Depending on the type of the property selected, the input will match the type. For example if we select **Lead Source**, the input will be a dropdown with the available **Lead Source** types. ![create-sf-lead6.png](./assets_v1714/create-a-salesforce-lead-v1714-5.png)


Summation
---------


In this guide we walked through creating one type of **Salesforce** object from within the connection builder using a Salesforce Integration. You can create any type of Salesforce object following similar steps. You can also find and update salesforce objects and even subscribe to object property changes with **Subscriptions**.