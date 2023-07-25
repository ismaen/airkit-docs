Every channel that allows for the initiation of an Airkit [Journey](https://support.airkit.com/docs/journeys) has an associated Event. This triggers the creation of a new Journey while also making it possible to take channel-specific [Actions](https://support.airkit.com/docs/action-builder) as soon as the Journey begins.


For example, when Starting Events pertain to users sending a text or making a phone call, this will almost inevitably trigger a Voice or Chat Bot, meaning that it is vital to perform the [Actor setup](https://support.airkit.com/reference/the-initialize-actor-action). (It is so vital, in fact, that Starting Events involving texts or phone calls now automatically include the Actor setup within its out-of-the-box Action Chain.)


# Working with Starting Events


A single app might have multiple Starting Events: one app might provide the option, for instance, for a user to start their Journey either by sending a text or clicking a link. New Starting Events can be added in either the Journey Builder or the Connection Builder, depending how the Journey starts:


* [Journey Builder](https://support.airkit.com/docs/journey-builder)  
  * Calls a Number - A Journey is triggered when a user calls a particular phone number.
  * Sends a Message -A Journey is triggered when a user sends a text message to a particular number.
* [Connection Builder](https://support.airkit.com/docs/connection-builder)  
  * Web Links - A Journey is triggered when a user navigates to a particular URL.
  * [API Calls](https://support.airkit.com/docs/creating-an-api-for-your-airkit-app) - A Journey is triggered when a call is made to the API associated with the application.
  * [Subscriptions](https://support.airkit.com/docs/passing-data-from-external-systems) - A Journey is triggered with data is passed from an external system.


To distinguish Starting Events that can be created in the Journey Builder from Starting Events that must be created under Connection Builder, the former are nested under the **Starting Events** section of the Tree, while the latter are nested under the **Integrations** section. For instance, if a Journey can begin with a user either clicking on a link or sending a text, the Journey Builder might appear as follows:


![2021-12-20_14-42-10.png](./assets_v1714/starting-events-v1714-0.png)


Note that both **Sends a message** and **Web Link** designate Starting Events.


Once a Starting Event has been added, the associated[Action Chain can be built out in the Journey Builder by examining the relevant Starting Event and opening the **Actions** tab in the Inspector.


## Accessing Event Input


Sometimes, such as when new Journeys are triggered by the [Journey Mapping Data Operation](https://support.airkit.com/reference/the-journey-mapping-data-operation), data is explicitly passed to Starting Event. Information passed to an Starting Event as input can be accessed within the associated Action Chain by referencing:



```javascript Airscript
event
```

For example, if a variable designated ```name``` is passed as input to a Starting Event, then to access its value within the downstream Action Chain, you would need to call on:



```javascript Airscript
event.name
```