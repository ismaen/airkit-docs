Overview
--------


Chat Bots manage automated phone call conversations that are part of a user's [Journey](https://support.airkit.com/docs/journeys). They can be used as [Events](doc:events)  to start a Journey or started as part of an Action Chain.


Chat Bots provide a way to tie text messages into a user Journey, making them a crucial part of [call deflection](https://support.airkit.com/docs/journeys), sending timed reminders, and otherwise following up with users.


Preparing the Web Page for the Chat Bot
---------------------------------------


The simplest example is to create a Chat Bot triggered from a Web Page, displaying information from the fields and to a phone number previously stored by the App.


Since the Chat Bot is triggered from a Web Page, first a [simple form](https://support.airkit.com/docs/building-a-simple-form) must be created.


In this example, the user will complete the form with their name and phone number. For each of these fields, a variable will be created automatically:


![chatvariabUPDATE.png](./assets_v1714/building-a-simple-chat-bot-v1714-0.png)


When the user clicks the “Track my order” button, an SMS will be sent to their phone number.


Three Actions must be added to the button for it to trigger the Chat Bot:


1. [Set Actor](https://support.airkit.com/docs/actors): to set the variable that will indicate the App to which number the Chat Bot must be sent
2. [Initialize Actor:](https://support.airkit.com/reference/the-initialize-actor-action) to set the values for the current Actor in the Journey
3. [Start Chat Bot](https://support.airkit.com/reference/the-start-chat-bot-action): to run the selected Chat Bot


![actionsMODIFIED.png](./assets_v1714/building-a-simple-chat-bot-v1714-1.png)


Creating the Chat Bot
---------------------


Chat Bots are created from the [Chat Bot Builder](https://support.airkit.com/docs/chat-bot-builder). 


Click on the '+' sign next to the Chat Bots and then select **Create Blank** or a Chat Bot Template.


![createchatbotred.png](./assets_v1714/building-a-simple-chat-bot-v1714-2.png)


From the Chat Bot level, in the **General** tab in the Inspector, add a Variable of type Text and rename it to "fullName". This way, you’ll be able to use the user’s name in the SMS.


![variablered.png](./assets_v1714/building-a-simple-chat-bot-v1714-3.png)


Add a Decision Menu and type the text that the SMS will display. Select **Expression** and enter the recently created ```fullName``` Variable so that the user is greeted by their name.


Then enter the Decision Options the user will receive upon following the Chat Bot indications. 


![exprefullname.png](./assets_v1714/building-a-simple-chat-bot-v1714-4.png)


We recommend adding transparent naming to all Chat Bot components to easily connect the Decision Options to each expected result.


Tying Variables
---------------


So that the ```fullName``` Variable created in the Chat Bot can reproduce the value entered in the “Name” input field, the Variable needs to be bound. 


Go back to [Web Builder](https://support.airkit.com/docs/web-builder) and in the Start Chat Bot action of the "Track my order" Button, an Input field will be displayed for you to enter the Variable:


![chatvariableUPDATE2.png](./assets_v1714/building-a-simple-chat-bot-v1714-5.png)


Now the **Expression** tag in the Chat Bot will retrieve the name entered by the user when the SMS is triggered.