Overview
--------


App notifications will inform you about your application’s errors through a channel of your choice. In this example, we will create a Slack app and link it to an App Notification so that messages are posted to a Slack channel.



#### Pre-requisites:


Before starting the configuration, create an #app-errors channel to receive the error messages in Slack.


Creating a Slack App
--------------------


To post messages from apps into Slack, a Slack App must be created with an Incoming Webhook. 


1. Go to  <https://api.slack.com/messaging/webhooks#getting_started> and click on Create your Slack app and then choose to create it from scratch. A modal will show up prompting you to name your app and then pick the workspace you’ll be using. Then click on Create App.


![C.png](./assets_v1714/configuring-app-error-notifications-to-slack-v1714-0.png)


2. Turn Incoming Webhooks on.

<img src="./assets_v1714/configuring-app-error-notifications-to-slack-v1714-1.png" alt="organizing info" style="max-width: 450px; width:100%"/>



3. Enter the Slack channel where notifications will be posted to.


<img src="./assets_v1714/configuring-app-error-notifications-to-slack-v1714-2.png" alt="organizing info" style="max-width: 450px; width:100%"/>

4. Scroll to the button to find the Slack app URL. 


![F.png](./assets_v1714/configuring-app-error-notifications-to-slack-v1714-3.png)


We recommend pasting the URL in the channel’s topic since it will be needed later on to create the App Notifier in the Console.


Adding the App Notifier to your Org
-----------------------------------


In the Console, go to Settings > Notifications and click on Create new.


<img src="./assets_v1714/configuring-app-error-notifications-to-slack-v1714-4.png" alt="organizing info" style="max-width: 400px; width:100%"/>

Choose a name for it, select Slack as Destination, paste the Slack app URL you have just created and click Create.


![HH.png](./assets_v1714/configuring-app-error-notifications-to-slack-v1714-5.png)


A Send Test button will show up for you to click and receive a Test text on the #app-errors channel: 


![I.png](./assets_v1714/configuring-app-error-notifications-to-slack-v1714-6.png)


Adding the App Notifier to your app
-----------------------------------


When publishing your app, click on Notifications and select the App Notifier you have previously created. Finally, click on Publish.


![J.png](./assets_v1714/configuring-app-error-notifications-to-slack-v1714-7.png)


From now on, all error messages will be posted into the Slack #app-errors channel.