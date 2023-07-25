In this document, we'll walk through the process of creating a Web Page that allows users to submit custom errors that are then [logged as a Custom Event](https://support.airkit.com/reference/log-custom-event-action) and flagged via an Email Notifier. 


The concepts covered in this document are relevant to the practicalities of using the [Log Custom Event Action](https://support.airkit.com/reference/log-custom-event-action) as well as [publishing an app](https://support.airkit.com/docs/publishing-your-application) so that errors that occur within it are not only logged but also submitted via Email Notifier. Similar concepts are covered in [Configuring App Error Notifications to Slack](https://support.airkit.com/docs/configuring-app-error-notifications-to-slack), which discusses Slack Notifiers as opposed to Email Notifiers and Application Errors as opposed to Custom Event Errors.


### Build the app


This section assumes you have already created an app and are working on it within the Web Builder in the Airkit Studio. The UI described can stand on its own if connected to a link in Journey Builder, or it can be part of a larger application flow.


1. Create a new Web Page and call it "Submit Error Web Page":


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-0.png" alt="organizing info" style="max-width: 350px; width:100%"/>

2. Add [Text Area Input Box Web Control](https://support.airkit.com/reference/text-area-web-control) to the "Submit Error Web Page". This is where users will submit their custom error messages. Note that, upon creation, the input is bound to the variable name **text_area**. Leave this as it is:


![2021-10-20_15-12-34.png](./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-1.png)


3. Add a [Button Web Control](https://support.airkit.com/reference/button-web-control) and change the associated text to "Submit Error":


![Screen_Shot_2021-10-20_at_3.14.00_PM.png](./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-2.png)


4. While still inspecting the "Submit Error" Button, open the **Actions** tab in the Inspector to open the Action Builder. Click on the '+' icon to the right of the **Clicked** branch and add a [Custom Log Event Action](https://support.airkit.com/reference/log-custom-event-action).


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-3.gif" alt="organizing info" style="max-width: 450px; width:100%"/>

5. Change the **Event Message** to "User submitted custom error", the **Log Level** to ERROR, and the **Metadata** to "User submitted the following message: {{**text_area**}}". Note the presence of quotation marks to designate strings, and the presence of double brackets to designate variables within those strings; this is required to be Airscript-parsable, and both **Event Message** and **Metadata** expect information in the form of Airscript:

<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-4.png" alt="organizing info" style="max-width: 300px; width:100%"/>


Upon completing the steps in this section, it is possible to publish this app as-is. The submitted error will be logged with the other [Airkit Events](https://support.airkit.com/docs/events); it can be accessed in the Console, under the Activity section.


### Set up Email Notifier


1. Save your changes, exit the Studio, and return to the Console. Access **Settings > Logs and Notifiers**.

<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-5.png" alt="organizing info" style="max-width: 150px; width:100%"/>



2. Scroll down to the **Notifiers** section and click on the associated **Create new** button.


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-6.png" alt="organizing info" style="max-width: 450px; width:100%"/>

3. Clicking on this button will open the Inspector, which will contain the tools to define the details of the new notifier being created. Name this new notifier "error_email_notification":


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-7.png" alt="organizing info" style="max-width: 400px; width:100%"/>

4. Under **Destination**, select **Email:**

<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-8.png" alt="organizing info" style="max-width: 400px; width:100%"/>

5. Once **Email** is selected under **Destination**, a new input box labeled **Email** will appear beneath it. Enter the email address that you want to send custom error notifications to. (You will need to check this email address to see related notifications, so make sure you enter an email address that you can easily access.)


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-9.png" alt="organizing info" style="max-width: 400px; width:100%"/>


6. Click on the **Create** button on the bottom right.

<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-10.png" alt="organizing info" style="max-width: 100px; width:100%"/>


7. Once a notifier is set up, you can test it by inspecting it and clicking on the **Send Test** button at the bottom of the Inspector. If properly set up, a test email should appear in the inbox of the designated email account.


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-11.png" alt="organizing info" style="max-width: 125px; width:100%"/>

Upon completing the steps in this section, you have created an Email Notifier. All apps within your [Organization](https://support.airkit.com/docs/airkit-organizations) will have access to this notifier. It can be used by any app to send errors of any kind. There are no limits to the number of errors types that can be associated with a single notifier.


### Publish Application


Most components of of Airkit apps can be tested by previewing them, but this is not the case with notifiers, because notifiers are set up as part of the [publishing](https://support.airkit.com/docs/publishing-your-application) process. In order to confirm that an Email Notifier is properly sent when a Custom Event Error is logged, the following publishing procedure must be done first:


1. Return to accessing your App in the Airkit Studio and publish your application by clicking on the **Publish** button on the upper right. This will open the following window:


![Screen_Shot_2021-10-20_at_4.26.18_PM.png](./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-12.png)


2. Expand the Notifications section:


![Screen_Shot_2021-10-20_at_4.27.12_PM.png](./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-13.png)


3. Under **Custom Log Error Event**, select **error_email_notification**.


![Screen_Shot_2021-10-20_at_4.27.44_PM.png](./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-14.png)


4. Click the *Publish* button on the bottom left of the window.


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-15.png" alt="organizing info" style="max-width: 100px; width:100%"/>

Upon completing the steps in this section, the application will be published, and any error submitted through the **Log Custom Event Action** will not only be logged with other the other [Airkit Events](https://support.airkit.com/docs/events), it will also be sent to the designated email address.


### Test it out!


1. Access the published application via the designated link. This will appear in the window that opens upon publication:


![Screen_Shot_2021-10-20_at_4.31.34_PM.png](./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-16.png)


It can also be found by inspecting the app in the Console:


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-17.png" alt="organizing info" style="max-width: 500px; width:100%"/>

2. Enter some test information in the text box and press the "Submit Error" button:


<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-18.png" alt="organizing info" style="max-width: 450px; width:100%"/>

3. Check the relevant email inbox and look for the error message. Note how the message appears so that you can see the **Event Message** ("User submitted custom error") associated with the [Log Custom Event Action](https://support.airkit.com/reference/log-custom-event-action), as well as the **Metadata** ("User submitted the following message: {{**text_area**}}"), which contains the test information as **text_area**.

<img src="./assets_v1714/how-to-log-a-custom-event-error-and-send-an-email-notifier-v1714-19.png" alt="organizing info" style="max-width: 450px; width:100%"/>