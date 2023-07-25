In the context of the Airkit platform, Events refer to any catalyst that might trigger an [Action Chain](https://support.airkit.com/docs/action-builder). All Action Chains are associated with a particular Event. It is when – and only when – an Event is fired that its associated Action Chain is performed.


# Conceptualizing Events

At its core, an Airkit Event is a piece of information that tells the platform something happened and might include optional metadata about the Actions that will consequently be taken. Not all Events will be associated with an Action Chain. An Event merely signals that the platform must check and see if there are any Actions to take. In this way, an Event like a letter: it's sent from somewhere, but ultimately once it gets to the recipient, the recipient decides what they do with it. The letter might spur some action, or it might be thrown directly in the trash.

When we say that Events tell the platform "something happened," we are being deliberately vague. All kind of things might trigger Events. A user clicking a [Button Web Control](https://support.airkit.com/reference/button-web-control) is an Event, as is the [instance before sending an SMS message](https://support.airkit.com/reference/decision-menu-control), as is updating a [Web Flow](https://support.airkit.com/docs/web-flows).


Built-in Events are fired from a variety of places in the Airkit platform, and you can also define Custom Events that are fired manually with the [Run Event Action](https://support.airkit.com/reference/the-run-event-action).







# The different types of Events


There are a few different types of Events in the Airkit platform. These different types of Events indicate how and where they can be invoked. The different types are:


* **Starting Events**: Start an Airkit [Journey](https://support.airkit.com/docs/journeys). These Events will commonly be triggered by things like the user clicking a specific link or texting a particular number.
* **Control Events**: Come out of the box with each Control and vary depending on the Control's functionality. For example, Buttons come associated with a single Event: '**Click**'. Text Input Boxes, on the other hand, come with three associated Events: '**On Blur**', '**Value Changed**', and '**On Enter**'.
* **Journey Events**: Global Custom Events that can be invoked anywhere in a Journey by the Run Event Action.
* **Activity Events**: Activity-level Custom Events that can be invoked by the Run Event Action. In contrast to Journey Events, Activity Events are only accessible within a specific Activity: an individual Web Flow, Chat Bot, or Voice Bot.
* **App APIs & Subscription Events**: Initiated whenever an API or subscription is triggered.