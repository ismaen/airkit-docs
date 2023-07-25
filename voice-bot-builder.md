The Voice Bot Builder provides the tools create automated phone experiences. This is the Builder you'll use to script outgoing messages and define how responses will be parsed and acknowledged.


Like most Builders, the layout of the Voice Bot Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector: 


![2021-12-08_14-40-40.png](./assets_v1714/voice-bot-builder-v1714-0.png)



# Tree


Displays an expandable and collapsible breakdown of the various components that have been built out as part of an automated phone experience, including each individual Voice Bot and its component Decision Menus. The Tree also provides the option to add additional components: clicking the '+' icon that appears when you run your mouse over a listed component provides the option to add a subcomponent that will be nested directly under said branch. 


These components and subcomponents are structured as follows:


* **[Voice Bots](https://support.airkit.com/docs/building-a-simple-voice-bot)** - Typically designed around a specific work flow.
   * **[Decision Menus](https://support.airkit.com/reference/decision-menu-control) - Defines two things: an outgoing message****and ways to parse and reply to different incoming responses.** Replies are defined by denoting another Decision Menu (or Voice Bot component on the same level of organization) to which the user will be directed.
   * **Decision Option**- define different ways a Voice Bot might parse and reply user input.
      * **Default Response** - defines how the Voice Bot will respond if it can't parse the reply it receives.
      * **Touchstone Capture**- Captures a pin or other [string](https://support.airkit.com/reference/the-text-variable-data-type) entered by the user and binds it to a variable.
      * **Secure Touchstone Capture**- Securely, via Redis key, captures a pin or other string entered by the user and binds it to a variable. The value associated with this variable can then be accessed with the [Secure Value Retrieval Data Operation](https://support.airkit.com/reference/the-secure-value-retrieval-data-operation).
      * **Forward Call**- Forwards the user to another phone number.
      * **Event**- Triggers an [Event](https://support.airkit.com/docs/events).


The Tree also enables the addition of one other component, which can nest under most subcomponents:


* **Expression** - reference the value of variables or other [Airscript](https://support.airkit.com/docs/airscript-quick-start) expressions in an outgoing message.


For a more detailed discussion on how to work with the component parts of a Voice Bot, check out [Creating a Simple Voice Bot](https://support.airkit.com/docs/building-a-simple-voice-bot).


# Stage


Displays a visual representation of the various components that make up an automated phone experience. Exactly what is displayed in the Stage varies to better communicate what component of the experience is being examined. For instance, when examining any part of a [Decision Menu](https://support.airkit.com/reference/decision-menu-control), the Stage will display the outgoing message (which will be said out loud by a text-to-speech program), the associated decision options, and the default response, like so: 

<img src="./assets_v1714/voice-bot-builder-v1714-1.png" alt="organizing info" style="max-width: 300px; width:100%"/>


On the other hand, when examining Touchstone Capture, the Stage will display only the outgoing message and the Decision Menu (or Voice Bot component on the same level of organization) that the user will be directed to once they have entered the [string](https://support.airkit.com/reference/the-text-variable-data-type) will be saved as the value of a variable:

<img src="./assets_v1714/voice-bot-builder-v1714-2.png" alt="organizing info" style="max-width: 350px; width:100%"/>

In both cases, outgoing or potentially outgoing messages can be edited directly in the Stage by clicking on the relevant text and making the desired edits.


For a more detailed discussion on how to work within the Voice Bot Stage, check out [Creating a Simple Voice Bot](https://support.airkit.com/docs/building-a-simple-voice-bot).


# Inspector


Provides the tools to examine and modify the individual elements that make up an automated phone experience and configure specific interactions associated with those elements. The layout of the Inspector will vary depending on the functionality of the element being inspected.

<img src="./assets_v1714/voice-bot-builder-v1714-3.png" alt="organizing info" style="max-width: 200px; width:100%"/>

In general, there are two tabs that may appear in the Voice Bot Builder Inspector: **General** and **Actions**. (Not every element will allow you to access both tabs while being inspected, because different elements allow different modifications.)


## General


Contains the fundamental information associated with the element being inspected. For instance, if inspecting a Voice Bot, the **General** Tab in the Inspector will display the relevant Events and variables, as well as initial greeting it will give a user. If inspecting a Decision Option, the Inspector will display all potential responses that the Decision Option will accept. Clicking on the '+' icon to upper right opens a pop-up window that allows you to select the type of new response you want to add: one that listens for a keyword ("Keyword Matcher") or one that parses a number entered on the dial pad ("DTMF Matcher").


## Actions


Under the **Actions** tab, you'll be able to access the Action Builder. This allows you to associate Action Chains with the any Events associating with the element you're inspecting.