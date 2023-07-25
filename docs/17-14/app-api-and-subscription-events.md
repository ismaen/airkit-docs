[App API and Subscriptions](https://support.airkit.com/docs/passing-data-from-external-systems) initiate Events if they successfully map to a [Journey](https://support.airkit.com/docs/journeys). This allow you to trigger an [Action Chain](https://support.airkit.com/docs/action-builder) associated with the incoming request.


For example, A [Salesforce subscription](https://support.airkit.com/docs/passing-data-from-external-systems) might associate incoming data with an Event that updates internal variables and sends a text to notify the user of the update. This would appear in the Journey Builder as something like the following:


![2021-12-21_12-29-09.png](./assets_v1714/app-api-and-subscription-events-v1714-0.png)


 App API and Subscription Events provide the ability to perform asynchronous actions on specific Journeys associated input from external systems.


# Working with App API and Subscription Events


App APIs and Subscriptions are configured in the Connection Builder. App APIs are nested under the **Web Links** section, Subscriptions are nested under the **Subscriptions** sections. Integrations might need to first be configured in the Console or Configuration Builder before becoming available; see [Connecting to External Systems](https://support.airkit.com/docs/connecting-to-external-systems) for more details.


Once an App API or Subscription Event has been added, the associated Action Chain can be built out in the Journey Builder by examining the relevant Event and opening the **Actions** tab in the Inspector.


## Accessing Event Input


Data that is captured from the incoming API call or Subscription can be handed over to the Event. Information passed as input can be accessed within the associated Action Chain by referencing:



```javascript Airscript
event
```

For example, if a variable designated ```name``` is passed as input, then to access its value within the downstream Action Chain, you would need to call on:



```javascript Airscript
event.name
```