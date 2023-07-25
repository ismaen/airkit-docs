The previous section discussed what Actors are and their significance in enabling omni-channel Journeys. Here, we take a deeper dive into how to apply the concept of Actors by examining their relevance in establishing text and phone communication channels, an important component of creating omni-channel Journeys.

# Chat Bots and Voice Bots

Text and phone conversations are managed through Chat Bots and Voice Bots respectively. Dialogue Bots (the collective term for Chat Bots and Voice Bots) define how incoming messages are parsed and responded to. Each one is typically designed around a conversation flow. A Dialogue Bot might, for instance, remind Actors of upcoming appointments, share order tracking information upon request, or ask Actors to complete a survey and walk them through the process of doing so. Chat Bots are defined and edited in the [Chat Bot Builder](doc:chat-bot-builder), Voice Bots in the [Voice Bot Builder](doc:voice-bot-builder). 

Dialogue Bots are triggered as Actions. Specifically, Chat Bots are triggered by the [Start Chat Bot](ref:the-start-chat-bot-action) Action and Voice Bots by the [Start Voice Bot](ref:the-start-voice-bot-action) Action. These Actions can be taken at any point after the Actor has been initialized. For a more detailed walkthrough of how to set up Dialogue Bots, see [Building a Simple Chat Bot](doc:building-a-simple-chat-bot) and [Building a Simple Voice Bot](doc:building-a-simple-voice-bot).

# Starting a Journey with an incoming call or text

When a Journey begins with an incoming call or text message, relevant starting parameters – such as the phone number and location of the caller – are saved automatically. (For more information on what information is automatically collected, see [Information Captured from Incoming Calls and SMS](doc:information-captured-from-incoming-calls-and-sms).) The phone number of the incoming message is saved under the Session Namespace, which allows the value of ```session.start``` to set the ```actor``` variable. From there, the Actor can be initialized.

All of this is set up automatically upon the creation of a **Calls a number** or **Sends a message** Starting Event. This is done in the [Journey Builder](doc:journey-builder), in the **Starting Events** section of the Tree. Upon creating a **Calls a number** or **Sends a message** Starting Event, you can examine them in the Inspector. The **Actions** Tab shows that the start of the Journey will trigger an Action Chain that comes out of the box with two Actions already set up: one that sets the value of the Actor, and one that initializes the Actor:

<img src="./assets_v1714/initializing-the-actor-v1714-0.png" alt="organizing info" style="max-width: 250px; width:100%"/>

<details>
  <summary>What number are these incoming texts and phone calls being sent to?</summary>

<br />

Whatever number you want to associate with the application!

The [Console](https://support.airkit.com/docs/console) provides the means to connect your phone numbers to your [Org](doc:airkit-organizations). Once connected to an Org, phone numbers will become available in the [Configuration Builder](doc:configuration-builder) when accessing your application in the Studio. Under the **Chat Bot** section, you can select an available number to receive, send, and manage texts associated with your application. Likewise, under the **Voice Bot** section, you can select an available number to receive, send, and manage associated calls.

Once a phone number is configured, incoming messages to that phone number through the designated channel will automatically be parsed as part of a Journey. For instance, suppose a phone number has been configured in the **Voice Bot** section of the Configuration Builder. If a Journey begins with the **Calls a number** Starting Event, any phone call made to the configured phone number will automatically trigger the start of a new Journey. Any outgoing calls will also be sent from the configured number.

For more on how to associate your phone numbers with Airkit apps, see [Connecting Your Twilio Numbers To Airkit](doc:connecting-your-twilio-numbers-to-airkit).

</details>

# Defining an Actor mid-Journey

When a Journey begins with an incoming call or text, Airkit can define and initialize the Actor by default, because the relevant data to do so is automatically collected, stored in the appropriate format, and bound to a pertinent variable. In cases where an Actor cannot be defined until a Journey is well underway, the Actions required to define and initialize the Actor must be explicitly set by the builder.

There are many ways to learn an Actor's phone number other than automatically collecting it from an incoming call or text. For instance, you could ask a user to give you their number directly via a form in a Web Flow, or you could pull their phone number from an external API. The varying means of collecting a phone number necessitate that you explicitly define which piece of incoming data be used to define the Actor. 

The process of doing so is largely a matter of replicating what is done by default when a phone number is collected through incoming calls and texts: first the phone number must be collected, then it must be used to set ```actor.phone```, then the Actor must be initialized.

**Step 1: Bind the phone number to a variable.** Phone numbers can be collected and bound to a variable just like any other value. For instance, if the number was collected via an input box in a form, data binding will occur as part of the functionality of the input box. Note that in order to be used to properly initialize an Actor, a phone number must be properly formatted.

<details>
  <summary>What does it mean for a phone number to be properly formatted?</summary>

<br />

Airkit expects phone numbers in the E.164 general format. Under the hood, Airkit uses the [ISPHONE](ref:isphone) function to test if a string contains a valid phone number. See reference documentation on ISPHONE for more details on how phone number must be formatted in order to be parseable. 

The function [PARSE_PHONE](ref:parse_phone) can be used to convert an improperly-formatted phone number into a format that Airkit can parse, and thus use to establish a phone or SMS channel.

</details>

**Step 2: Use the [Set Variable](ref:the-set-variable-action) Action to set the value of ```actor.phone```.**

**Step 3: Use the [Initialize Actor](ref:the-initialize-actor-action) Action to initialize the Actor.**

Once an Actor is initialized, voice and SMS channels will be established automatically. All incoming texts and calls from this phone number will be considered part of the ongoing Journey. All outgoing texts and calls will likewise be sent to the established phone number.