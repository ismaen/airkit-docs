This article covers how to set up Google Tag Manager to collect and organize data on how users interact with your Airkit apps.

### Prerequisites

- Access to a [Google Tag Manager account, container, and container ID](https://tagmanager.google.com/#/home).
- Passing familiarity with how to set up tags and triggers within Tag Manager. (To learn more about tags, triggers, and collecting data within Tag Manager, check out [their documentation site](https://developers.google.com/tag-platform/tag-manager/web).)

### Declare Google Tags Manager the analytics provider of your app

Setting up Tags Manager so that it can begin handling the analytics of your website begins by installing the Tags Manager and declaring what container your data will be associated with. (Outside of Airkit, this is often done by inserting code into the relevant web pages, see documentation [here](https://developers.google.com/tag-platform/tag-manager/web).) This is done via the following steps:

1. Open the app that you want to associate with Tag Manager in the [Studio](https://support.airkit.com/docs/studio).

2. Toggle down to the [Configuration Builder](https://support.airkit.com/docs/configuration-builder) and scroll down to the **Analytics** section.

3. Under Provider, select "Google Tag Manager".

4. Under ID, enter your Tag Manager container ID, which should be in the format `GTM-XXXXXX`. (The container ID defines the container within Tag Manager that will store analytics related to this app. The containers accessible to you as well as their associated IDs should be visible upon visiting [Google's Tag Manager home page](https://tagmanager.google.com/#/home); their [documentation](https://developers.google.com/tag-platform/tag-manager/web) also describes how to find and utilize your container IDs.)

Upon completion, the **Analytics** section of the Configuration Builder should look as follows, with the "X"s under ID replaced with the value of your own Tag Manger container ID:

![2021-12-01_16-06-45.png](./assets_v1714/setting-up-analytics-with-google-tag-manager-v1714-0.png)

Save your changes. Installation of Tag Manager is now complete and includes the creation and installation of the optional [data layer](https://developers.google.com/tag-platform/tag-manager/web/datalayer) object. 

### Log Page Views

Once Tag Manager is installed and the application is published, Airkit will automatically send a custom page tracking event to the [data layer](https://developers.google.com/tag-platform/tag-manager/web/datalayer) every time a user navigates to another [Web Flow](https://support.airkit.com/docs/web-flows) or Web Page. This custom page tracking event is sent in a JSON object with the following format, where **Web_Flow** and **Web_Page** correspond to the names of the Web Flow and Web Page (respectively) that the user just navigated to:

```json JSON
{
    "event": "Page Navigate",
    "properties": {
        "Page-Name": Web_Flow,
        "View-Name": Web_Page
    }
}
```



While this custom page tracking event will automatically be sent to the data layer, a tag and custom event trigger must be set up so that the sent information can be properly parsed. To read more about triggers and custom events within Tag Manager, click [here](https://developers.google.com/tag-platform/tag-manager/web/datalayer). 

### Send Custom Events

In addition to automatically sending a custom page tracking event to the data layer every time a user navigates to another Web Page, Airkit also provides the tools to send a custom payload at any time, using the [Analytics Send Event Action](https://support.airkit.com/reference/analytics-send-event-action), which will send a JSON object in the following format:

```json JSON
{
    "event": Event_Name,
    "properties": Event_Properties
}
```



**Event_Name** and **Event_Properties** correspond to values entered in the [Analytics Send Event Action](https://support.airkit.com/reference/analytics-send-event-action) under "Event Name" and "Event Properties", respectively.

As with logging page views, a a tag and custom event trigger must be set up so that the sent information can be properly parsed. To read more about triggers and custom events within Tag Manager, click [here](https://developers.google.com/tag-platform/tag-manager/web/datalayer).