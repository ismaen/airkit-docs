Activity Events are can be initiated anywhere throughout a specific Activity. Activities include individual [Web Flows](https://support.airkit.com/docs/web-flows), [Chat Bots](https://support.airkit.com/docs/chat-bot-builder), and [Voice Bots](https://support.airkit.com/docs/voice-bot-builder): Web Flow Events, Chat Bot Events, and Chat Bot Events are subcategories of Activity Events. For example, Activity Event tied to a Web Flow is a Web Flow Event.


Activity Events are used to encapsulate meaningful, reusable [Action Chains](https://support.airkit.com/docs/action-builder) as well as to elevate meaningful interactions within an Activity that are meant to connect with the larger Journey: Activity Events (and their associated Action Chains) are illustrated in the Journey Builder, whereas individual Control Events are not. This makes Activity Events particularly valuable when using the Journey Builder to connect [Kitcloud Templates](https://support.airkit.com/docs/kitcloud).


The following example shows how the [Capture Customer Info Web Flow](https://support.airkit.com/reference/capture-customer-info-web-flow) appears upon being added in the Journey Builder. Note how the Activity Event, "Contact Info Captured" appears. It is visible in Tree and the Stage as well as capable of being edited in the Inspector:


![2021-12-20_09-55-20.png](./assets_v1714/activity-events-v1714-0.png)


One common use of Activity Events is to create a final Action Chain that occurs when an Activity's purpose is complete. This is the purpose of the Activity Event shown in the example above: once the Customer has finished filling out their information, their input can be passed to the "Contact Info Captured" Event for use in the downstream Action Chain. 


# Working with Activity Events


Activity Events are created in the Web Builder, Chat Bot Builder, or Voice Bot Builder, depending on whether the Activity Event is associated with a Web Flow, Chat Bot, or Voice Bot. Inspect the relevant Activity and click on the '+' icon that appears to the right of the **Web Flow/Chat Bot/Voice Bot Events** section of the Tree.


Once created, Activity Events are edited in the Journey Builder, where they can be found nested under their associated Activity in the Tree. Clicking on an Activity Event opens it in the Inspector. Clicking on the **Actions** tab opens the Action Builder; this is where you'll build out the Action Chain that you want to associate with your Activity Event. Under the **General** tab, you can also define variables that the Activity Event will expect as input, allowing you to pass input to the Event for use in the downstream Action Chain.


## Accessing Event Input


Information passed to an Activity Event as input can be accessed within the associated Action Chain by referencing:



```javascript Airscript
event
```

As an example, consider the "Contact Info Captured" from the Capture Customer Info Web Flow shown above. To access the value given for ```first_name``` within the downstream Action Chain, you would need to call on:



```javascript Airscript
event.first_name
```