This article covers how to set up Heap to collect and organize data on how users interact with your Airkit apps.

### Prerequisites

- Access to [a Heap account](https://heapanalytics.com/login?redirect=%2Fapp%2Fmanage%2Fprojects)
- Passing familiarity with how to conceptualize Heap and when to call the identify API. For Heap's documentation on the topic, click [here](https://developers.heap.io/docs/using-identify).

### Declare Heap the analytics provider of your app

Setting up Heap so that it can begin handling the analytics of your website begins by installing Heap. (Outside of Airkit, this is often done by inserting code into the relevant web pages, see documentation [here](https://developers.heap.io/docs/web).) This is done via the following steps:

1. Open the app that you want to associate with Tag Manager in the [Studio](https://support.airkit.com/docs/studio).

2. Toggle down to the [Configuration Builder](https://support.airkit.com/docs/configuration-builder) and scroll down to the **Analytics** section.

3. Under Provider, select "Heap".

4. Under ID, enter the app ID of the environment to which you want to send data. This ID is provided by Heap; you can find it on the [Projects](https://heapanalytics.com/app/manage/projects) page. (For more on how to find locate a particular app ID, check out Heap's [documentation site](https://developers.heap.io/docs/web).)

Upon completion, the **Analytics** section of the Configuration Builder should look as follows, with the "X"s under ID replaced with the value of your own app ID:

![2021-12-02_13-56-17.png](./assets_v1714/setting-up-analytics-with-heap-v1714-0.png)

Save your changes. Installation of Heap is now complete. Once the application is published, Heap will be free to automatically collect data on user interactions.

### Call identify

In order for Heap to associate gathered information with a user, a call must be made to Heap's identify API that declares the user's identity. This can be done at any point throughout a user's [Journey](https://support.airkit.com/docs/journeys), but the typical and recommended time for an identify call is on any post-login or post-signup page. (Assigning an identity to a user when it has not been confirmed can lead to undesirable or unexpected behavior.) Pertinent data gathered both before and after the action will then be stored under the designated identity. For more information on how to conceptualize calling identify within the context of Heap, check out [Heap's documentation](https://developers.heap.io/docs/using-identify) on the subject.

Here's how to incorporate calling Heap's identify API within the flow of an Airkit App:

1. Toggle over to the [Web Builder](https://support.airkit.com/docs/web-builder) and inspect the element that you want to associate with calling identify. (Common elements to associate with calling identify include a confirmation button or a post-signup page.)

2. Open the [Action Builder](https://support.airkit.com/docs/action-builder) within the Inspector.

3. Click on the '+' icon next to the relevant even in the Action Builder and select the [Analytics Identify Action](https://support.airkit.com/reference/analytics-identify-action) from the resulting pop-up menu.

4. Enter the [string](https://support.airkit.com/reference/the-text-variable-data-type) designating the identity of the user into the input box under **Identity**. Note that this string must be unique to each user, meaning best practice dictates that this string must be given in the form of an [Airscript](https://support.airkit.com/docs/airscript-quick-start) expression rather than hardcoded. 

### Send Custom Events

To supplement data Heap automatically collects, Airkit provides the tools to send a custom payload at any time. This can be used, for instance, to track buttons clicked or to track logic paths traversed via Airscript. It is archived via the [Analytics Send Event Action](https://support.airkit.com/reference/analytics-send-event-action), which will send a JSON object in the following format:

```json JSON
{
    "event": Event_Name,
    "properties": Event_Properties
}
```



**Event_Name** and **Event_Properties** correspond to values entered in the [Analytics Send Event Action](https://support.airkit.com/reference/analytics-send-event-action) under "Event Name" and "Event Properties", respectively.

This JSON object, like all events, is sent client-side, using the `track` method in Heap's web API. For to access Heap's documentation on the track method, click [here](https://developers.heap.io/reference/track). 

### A note on security

When Heap is loaded into an Airkit-created app, Airkit sets the `disableTextCapture` property to **FALSE** and the `secureCookie` property to **TRUE**. This ensures that the text on the page is redacted. See relevant Heap documentation on redacted text capture and secure Cookes [link](https://developers.heap.io/docs/web#disabletextcapture) and [here](https://developers.heap.io/docs/web#securecookie) respectively.