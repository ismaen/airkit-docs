Journey Events are globally available Events that can be initiated anywhere throughout a [Journey](https://support.airkit.com/docs/journeys). Typically, these are used to encapsulate meaningful, reusable [Action Chains](https://support.airkit.com/docs/action-builder).  


For example, a "Reminder Message" Event might [log a metric](https://support.airkit.com/reference/the-reporting-metric-count-action), [initiate a reminder message Chat Bot](https://support.airkit.com/reference/the-start-chat-bot-action), and [schedule](https://support.airkit.com/reference/the-create-timer-action) a follow up reminder for the next day. This Event can be triggered at any point in the Journey.


 Here's how that "Reminder Message" Event might appear in the Journey Builder. Note that, unlike Activity Events, it is not tied to a single Activity: 


![2021-12-20_12-52-58.png](./assets_v1714/journey-events-v1714-0.png)


# Working with Journey Events


Journey Events are created in the Journey Builder by clicking on the '+' icon to the right of the **Journey Events** branch, which is nested under the **Journey** section of the Tree. Once created, Journey Events can be edited in the Inspector. Clicking on the **Actions** tab opens the Action Builder; this is where you'll build out the Action Chain that you want to associate with your events. Under the **General** tab, you can also define variables that the Journey Event will expect as input, allowing you to build out general-purpose Action Chains that behave differently depending not only on user input but also when and how they are called within a Journey.


Journey Events are fired by the [Run Event Action](https://support.airkit.com/reference/the-run-event-action), which must be built out as part of a separate Action Chain.


## Accessing Event Input


Information passed to a Journey Event as input can be accessed within the associated Action Chain by referencing:



```javascript Airscript
event
```

For example, if a variable designated ```name``` is passed as input to a Journey Event, then to access its value within the downstream Action Chain, you would need to call on:



```javascript Airscript
event.name
```