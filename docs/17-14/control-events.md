Control [Events](https://support.airkit.com/docs/events) are tied to individual Controls and the specific user interactions they allow. Controls that allow for direct users interactions will have an **Actions** tab in the Inspector. Opening the [Action Builder](https://support.airkit.com/docs/action-builder) in this tab will display Events associated with every type of interaction a user could have with that Control. Separate Action Chains can be built under each Event.


Some Controls, such as [Button](https://support.airkit.com/reference/button-web-control), lend themselves to only a single type of interaction (clicking the button), and thus only have one Event ("**Click**"):


![2021-12-17_12-37-11.png](./assets_v1714/control-events-v1714-0.png)


Other Controls, such as [Text Input Boxes](https://support.airkit.com/reference/text-input-web-control), lend themselves to being interacted with in multiple ways (clicking on the input box, typing something in the input box, and clicking away from the input box), and thus have multiple Events ("**On Blur**", "**Value Changed**", and "**On Enter**".)


# Working with Control Events


Control Events can be found in the **Actions** tab in the Inspector whenever you're examining a Control that allows direct interaction from users. Be aware that not all Controls allow such direct interaction. The Label Web Control, for instance, provides text that users are intended to read, but users cannot click on the text or otherwise provide it with any direct input.


Controls are found across multiple Builders. As a rule of thumb, Web Controls are accessed in the Web Builder and Dialogue Controls as accessed in the Chat Bot Builder and Voice Bot Builder.


## Event Values


Some Control Events pass information to the Action Chain they trigger. In such cases, this information can be accessed within the associated Action Chain by referencing:



```javascript Airscript
event.value
```

The format of the information stored in ```event.value``` changes depending on the nature of the Event. For a deeper dive into the different structures ```event.value``` can take, compare how it is used in Action Chains triggered by the [Secure Text Input Web Control](https://support.airkit.com/reference/secure-text-input-web-control) (in which it contains a string) vs. the [Schedule Web Control](https://support.airkit.com/reference/scheduler-web-control) (in which it contains a Schedule App Object).