The Journey Builder is the Builder that you'll be taken to automatically each time you create a new application. It provides a big-picture view of how the component pieces of your app fit together, allowing you to visualize and modify the flow of a [Journey](https://support.airkit.com/docs/journeys) from start to finish. This is where you'll establish the entry points to your Airkit App, configure different [Events](https://support.airkit.com/docs/events) that occur within your Journey, and access [Kitcloud](https://support.airkit.com/docs/kitcloud) templates. 


Like most Builders, the layout of the Journey Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector:
 
![Journey Builder.png](./assets_v1714/journey-builder-v1714-0.png)

# Tree


The Tree is where you'll find an expandable and collapsible breakdown of the big-picture components that make up a Journey. This includes triggers that might begin a Journey, like Starting Events and Integrations, as well as the Web Flows and conversational bots that users might go through while journeying through your app. 


## Starting Events


Starting Events are [Events](https://support.airkit.com/docs/events) that trigger the start of a Journey. A single app might have multiple Starting Events: one app might provide the option, for instance, for a user start their Journey either by sending a text or making a phone call.


There are two Starting Events that can be added in Journey Builder:


* *Calls a Number* - A Journey is triggered when a user calls a particular phone number.
* *Sends a Message* - A Journey is triggered when a user sends a text message to a particular number.


These Starting Events can be added by clicking the '+' icon to the right of the **Starting Events** branch in the Tree and deleted by clicking the trash icon to the right of them:


![2021-06-30_16-45-28__1_.gif](./assets_v1714/journey-builder-v1714-1).gif)


There are ways to trigger the start of a Journey that cannot be added in Journey Builder, such as having potential users click on a link. While these sorts of triggers are also technically "Starting Events", they are nested under the Integrations branch of the Tree to distinguish them from obligate Starting Events that can be added directly in the Journey Builder. (Journeys that begin with an incoming call or text also [automatically capture the same information at the start of a session](https://support.airkit.com/docs/information-captured-from-incoming-calls-and-sms), which is another reason they are clustered together here.)


## Integrations


Under the **Integrations** branch, you'll find all the potential but not obligate Starting Events, the ones that that can't directly be added in Journey Builder. These include API calls, Web Links, and [Subscriptions](https://support.airkit.com/docs/passing-data-from-external-systems), all of which can be added in the [Connection Builder](https://support.airkit.com/docs/connection-builder). These will appear in the Journey Builder Tree automatically upon being added.


The following example shows how this branch of the Tree might appear after a subscription (**Chandra Spotify**), an App API (**App API**) and Web Link (**Web**) have all been added in the Connection Builder:

<img src="./assets_v1714/journey-builder-v1714-2.png" alt="organizing info" style="max-width: 250px; width:100%"/>


## Journey


Under the **Journey** branch, you'll have access to Journey-level Events, allowing you to examine and modify the behaviors associated with them.

<img src="./assets_v1714/journey-builder-v1714-3.png" alt="organizing info" style="max-width: 250px; width:100%"/>


* **Journey Started** - Define what happens as soon as a Journey starts, regardless of what Starting Event triggered the Journey. By default, as soon as you create an app, starting a Journey will trigger two actions: [setting the Actor variable](https://support.airkit.com/reference/the-set-variable-action) and [initializing the Actor](https://support.airkit.com/reference/the-initialize-actor-action). For more on Starting Events, see [Starting Events](doc:starting-events).


* **Journey Ended** - Define what happens immediately after a Journey ends. Perhaps you want to [run one last data flow](https://support.airkit.com/reference/the-run-data-flow-action) or [log a metric for reporting](https://support.airkit.com/reference/the-reporting-metric-count-action).


* **Journey Events** - Create custom Journey Events that can be triggered as Actions. These Events are used to create a reusable Action Chain that can be triggered from any part of your application flow. For more on Journey Events, check out [Journey Events](doc:journey-events).


## Web


This branch contains all of the [Web Flows](https://support.airkit.com/docs/web-flows) associated with your app. Accessing these provides the same functionality as accessing the [Web Flow level in the Web Builder](https://support.airkit.com/docs/web-builder).


## Chat Bots


This branch contains all of the [Chat Bots](https://support.airkit.com/docs/building-a-simple-chat-bot) associated with your app. Accessing these provides the same functionality as accessing the [Chat Bot level in the Chat Bot Builder](doc:chat-bot-builder).


## Voice Bots


This branch contains all of the [Voice Bots](https://support.airkit.com/docs/building-a-simple-voice-bot) associated with your app. Accessing these provides the same functionality as accessing the [Voice Bot level Voice Bot Builder](doc:voice-bot-builder).


# Stage


The Stage displays a map of the various elements of a Journey – including Starting Events, Journey Events, Web Flows, Chat Bots, and Voice Bots – and how they all fit together.


The follow example shows how the stage will appear when working on an app with a relatively simple Journey flow. A user will click on a link, which will take them to the [Web Flow](https://support.airkit.com/docs/web-flows) **Three Buttons Prompt**. From there, the user will have the opportunity to trigger the event **Button Selected**, which will lead them to the Web Flow **Capture Customer Info**. Once again, the user will then have the opportunity to trigger an Event – this one called **Contact Info Capture** – at which point they will be taken to the Web Flow **Thank You Page**:


![2021-06-30_16-38-37.png](./assets_v1714/journey-builder-v1714-4.png)


Journeys can be arbitrarily complicated; the map displayed in the Stage can become far more intricate than the one displayed above.


The Stage is also where you'll be able to add and connect additional elements, including [Kitcloud](https://support.airkit.com/docs/kitcloud) templates. Clicking the '+' icon attached to an Event allows you to declare what that will follow that Event. The following example shows how the Kitcloud Web Flow Template **Three Buttons Prompt** can be set as the first Web Flow to appear when a user clicks a link:


![2021-06-30_17-25-53__1_.gif](./assets_v1714/journey-builder-v1714-5).gif)


# Inspector


The Inspector is where you can examine and modify the individual elements that make up your application; in the Journey Builder, this is what you'll use to associate variables with certain elements and declare how the app should behave when various Events are triggered. To better reflect the functionality of the Inspector, its layout changes subtly even when being used to examine relatively similar things.


In general, there are three tabs you might find in the Journey Builder Inspector: **General**, **Actions**, and **Advanced**. (Not every element will allow you to access each tab while being inspected, because different allow different modifications.)


## General


Find general information regarding the element being inspected, such as the Events and variables associated with a particular Activity Group, and set the Activity that the Activity Group leads with (such as the first page of a Web Flow or the initial prompt given by a Chat Bot).

The **General** tab is only accessible when inspecting Web Flows, Chat Bots, or Voice Bots, which are collectively referred to as **Activity Groups**.


## Actions


Access the Action Builder. This allows you to associate Action Chains with the any Events associating with the element you're inspecting. 


## Advanced


As a rule of thumb, the **Advanced** tab provides the ability to inspect and edit any functionality that will vary across components in Airkit. Most commonly, the **Advanced** tab will appear when examining an Event, and subsequently provide the internal ID of the Event Handler.