Overview
--------


Voice Bots manage automated phone call conversations that are part of a user's [Journey](https://support.airkit.com/docs/journeys). They can be used as [Events](doc:events) to start a Journey or started as part of an Action Chain.


Voice Bots provide a way to tie phone calls into a user Journey, making them a crucial part of [call deflection](https://support.airkit.com/docs/building-a-call-deflection-app), following up with users, and [automating the process of managing scheduled phone calls](https://support.airkit.com/docs/using-the-scheduler-web-control-to-reschedule-deflected-calls).


Preparing the Web Page for the Voice Bot
----------------------------------------


The simplest example is to create a Voice Bot triggered from a Web Page to a phone number previously stored by the App.


Since the Voice Bot is triggered from a Web Page and the user will receive a phone call with an SMS option, a [simple form](https://support.airkit.com/docs/building-a-simple-form) and a Chat Bot must be created first.


In this example, the user will complete the form with their name and phone number and, when clicking on the “Track my order” button, a phone call will be triggered to their phone number.


 


![simplechatbot1.png](./assets_v1714/building-a-simple-voice-bot-v1714-0.png)


Three Actions must be added to the button for it to trigger the Voice Bot:


1. [Set Actor](https://support.airkit.com/docs/actors): to set the variable that will indicate to the App which number to call
2. [Initialize Actor](https://support.airkit.com/reference/the-initialize-actor-action): to set the values for the current Actor in the Journey
3. [Start Voice Bot](https://support.airkit.com/reference/the-start-voice-bot-action): to run the selected Voice Bot


![startvoicefromwebpage.png](./assets_v1714/building-a-simple-voice-bot-v1714-1.png)


Creating the Voice Bot itself
-----------------------------


Voice Bots are created from the [Voice Bot Builder](https://support.airkit.com/docs/voice-bot-builder). 


Click on the '+' sign next to Voice Bots and then select **Create Blank** or a Voice Bot Template.


![createvoicebotred.png](./assets_v1714/building-a-simple-voice-bot-v1714-2.png)


Select [Decision Menu](https://support.airkit.com/reference/decision-menu-control) and type the message the user will listen to. Next, enter the Decision Options the user will receive upon following the Voice Bot indications. 


Use the Keyword Matcher to capture voice responses or the DTMF Matcher to capture pressed keys on the phone.


 


![voice2.png](./assets_v1714/building-a-simple-voice-bot-v1714-3.png)


In this example, “Response 2” will allow the user to perform self-service. To configure “Response 2”, go to its Decision Menu and, in Actions, select **Start Chat Bot** from **After Voice Prompt** and pick the corresponding [Chat Bot](https://support.airkit.com/docs/building-a-simple-chat-bot).


![startchatbotmodified.png](./assets_v1714/building-a-simple-voice-bot-v1714-4.png)


This way, after pressing the self-service option, the user will receive an SMS to continue to self-service from the Web Flow.


Finally, [Style Variants](https://support.airkit.com/reference/common-style-properties-of-web-controls) can be added to Voice Bots to customize the message.


 


![stylevariant.png](./assets_v1714/building-a-simple-voice-bot-v1714-5.png)


We recommend adding transparent naming to all Voice Bot components to easily connect the  Decision Options to each expected result.