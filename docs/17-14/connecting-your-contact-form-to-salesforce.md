This article covers how to connect the Contact Form app built in the earlier sections to Salesforce, making it possible to save or update users’ information as a Salesforce Contact through the application.


#### Prerequisite


You will need to have a Salesforce account or developer instance in order to create a Salesforce integration in Airkit. To sign up for a salesforce developer account, go to <https://developer.salesforce.com/signup>.

You will also need access to the Contact Form described in the previous article.

![01.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-0.png)


Adding a CSAT modal to your Contact Form
----------------------------------------


Here you will initiate a CSAT (customer satisfaction) modal to pop up once the user enters in their information and clicks on the "Submit" button.


The CSAT modal will be added from [KitCloud](https://support.airkit.com/docs/kitcloud). 


1. In Web Builder, click on the '+' icon next to Web Flows to open KitCloud and select the CSAT template from the Customer Experience options.


![02.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-1.png)


2. Now that the CSAT template is added as a new Web Flow, select the type of CSAT you want to keep. In this example, the CSAT with square edges will be used:


![03.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-2.png)


The other two options can be deleted:


![04.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-3.png)


Triggering the Modal from the Contact Form Web Flow
---------------------------------------------------


1. In Web Builder, go to the “Submit” button in the Contact Info Web Page.


2. In the Inspector section, click on Actions. You will see the Navigate to Web Flow Action leading users to the Thank You page after submitting the form.


![05.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-4.png) 


3. Now, click on the '+'  icon and add the Open Modal Action from the Web options. A Modal allows Web Flows to behave like popups.


![06.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-5.png)  



4. Select the CSAT Web Flow.


![07.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-6.png)


Integrating Salesforce to your application
------------------------------------------


Integrations are how external systems connect within Airkit. You’ll start configuring the integration in the Console and then continue in the Studio.


### In the Console


1. Go to Integrations. Click on **Create new**, type a name and select the Salesforce integration. Then click on **Create**.


![08.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-7.png)


If you are not logged into your Salesforce instance, a popup will display asking you to enter your credentials.


### In the Studio


1. Access your Contact Form app and go to Configuration Builder. This is where you connect your resources to Airkit. Scroll down to Integrations and click on **New**. Then select **Salesforce** from the **Adapters**.


![09.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-8.png)  



2. In Connected Account, select from the dropdown the one you have just created in the Console.


![10.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-9.png)


3. Save the app.


Adding a Data Operation to connect to Salesforce
------------------------------------------------


This section will go over the Salesforce Data Operation. 


1. First, go to Connection Builder.


2. In Connection Builder, you will see the “Insert Content” Data Flow that was added when the Contact Form was built in the previous section. Add the Salesforce data operation to it by clicking on the '+' icon. Search for Salesforce and select it.


![11.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-10.png)


3. In **Datasource**, select "Salesforce", which is the name of the integration previously created, and under **Operation**, select the type of action you want to perform. In this case, it’s going to be the creation of a new record.


![12.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-11.png)


4. In** Object Type**, select **Contact**. The Object Body displays the properties you need to create a Contact Object. In this case it requires a Last Name, so the ```name``` Variable in your Contact Form needs to be passed here. Add the other fields one by one: ```phone```, ```email``` and ```company```.


![13.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-12.png)


5. You can do a quick test within this Data Operation by clicking on **Run**:


![14.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-13.png)


The record should be created in Salesforce. Take note of the "id" property 


Adding the Transform Data Operation to parse the Salesforce ID
--------------------------------------------------------------


To continue with the Web Flow, after clicking on “Submit”, the CSAT Modal will open for users to select a score. That score will be recorded and then that information will also be passed to the user’s record, thus updating it.


To perform updates, Salesforce requires you to have the ID of the records, which we will be saved as a global variable in the app. 


1. In Connection Builder, click on the ```Salesforce``` Variable. This Variable contains the output of the operation that was run.


![15.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-14.png)


2. Add a Transform Data Operation to the Data Flow in order to parse the output of the previous operation.


![16.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-15.png)


3. In Transform Expression, enter the ```Salesforce``` Variable and parse through the variable by appending “.result.id” to the end. This way only the ID is shown. Then select Type Text so that you can read the value without the JSON format. Then rename the ```Transform``` Variable with a more intuitive, like “SalesforceID”.



```javascript Airscript
Salesforce.result.id
```

![17.png](https://a01-support.airkit.com/connecting-your-contact-form-to-salesforce/17.png)


4. Finally, select “SalesforceID” as the End Return Value. This will allow you to pass the ID as an output of the Data Flow.


![18.png](https://a01-support.airkit.com/connecting-your-contact-form-to-salesforce/18.png)


Creating a new Data Flow to update records
------------------------------------------


This will be used later on to pass the CSAT score and comments associated to update the record in Salesforce. This will be visited when configuring the CSAT Web Flow.


1. In Connection Builder, click on the Create Blank to add a new Data Flow. Rename it to "Update Record".


![19.png](https://a01-support.airkit.com/connecting-your-contact-form-to-salesforce/19.png)


2. As Inputs, create the following three variables of type Text one by one: ```Salesforce_id```, ```CSAT``` and ```Feedback```. These variables will allow you to pass in the content from the CSAT Web Flow to this Data Flow.


![20.png](https://a01-support.airkit.com/connecting-your-contact-form-to-salesforce/20.png)


3. Add the Salesforce Data Operation. In **Datasource**, select **Salesforce**. In Operation, this time add Update record.


![21.png](https://a01-support.airkit.com/connecting-your-contact-form-to-salesforce/21.png)


4. In **Object Type**, select **Contact** and then, check the **Custom Expression** box to enter your ```Salesforce_id``` variable in the required id field. Finally, since this Data Flow was created to add the information on the CSAT Web Flow to the record, in Update Body, select **Contact Description** (this is where the info will be stored in the Salesforce record) and then pass the CSAT and Feedback Variables:



```javascript Airscript
CONCAT(CSAT, “-”, Feedback)
```

![22.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-16.png)


When it comes the turn to configure the Event, this Data Flow will be ready to be used.


Creating a global variable for the Salesforce ID
------------------------------------------------


By creating a global variable that stores the SalesforceID, you will be able to pass it across Web Flows.


1. Go to Journey Builder and, in the **General** tab of the Inspector section, click on the '+' icon next to Global Variables. Select a Text type and rename it to "salesforce_id".


![23.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-17.png)


Connecting the Data Flow to the Web Flow
----------------------------------------


So that the user’s information can be stored in the ```salesforce_id``` Variable, you need to connect the Data Flow to the “Submit” button in the Contact Form Web Flow.


1. Go to Web Builder and, in the “Submit” button, add the Run Data Flow action.


![24.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-18.png)  



2. Select the “Insert Content” Data Flow and pass the input variables for each of the fields in the form. Finally, in **Output Binding**, enter the recently created global variable:



```javascript Airscript
session.salesforce_id
```

![25.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-19.png)


3. Now go to the CSAT Web Flow. In the “Submit feedback” button actions, you will see a pre-configured event. If you click on it, you can see the Inputs that are passing the score and the feedback:


![26.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-20.png)  



4. Go back to Journey Builder and click on the CSAT Selected Event. In the Action Builder, add a new Data Flow. Finally, select the “Update record” Data Flow and as Inputs, select the variables corresponding to the Salesforce ID, CSAT score and Feedback fields.


![27.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-21.png)


5. Save the app.


Previewing the application
--------------------------


Once the app is all set, it can be tested in the App Preview.


1. Click on Preview at the right-hand corner of the Studio, which will open a new tab.


![28.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-22.png)  



2. Click on the globe icon, which allows the app to be launched from the start.


![29.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-23.png)


3. Complete the fields and click on “Submit”.


![30.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-24.png)


As expected, the CSAT Modal will pop up for the user to select the score and add some feedback. 


![31.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-25.png)


Verifying Contact was created in Salesforce and updated with CSAT
-----------------------------------------------------------------


1. Sign into your Salesforce account or developer instance, click on the App Launcher icon and select Sales Console.


![32.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-26.png)  



2. Once in the Sales Console, click on the arrow icon and select Contacts.


![33.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-27.png)


3. Identify the user that was created through the Airkit application. The record should be added updated in Salesforce with the CSAT details in the contact description:


![35.png](./assets_v1714/connecting-your-contact-form-to-salesforce-v1714-28.png)