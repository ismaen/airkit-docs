The Chat Bot Builder provides the tools create SMS experiences. This is the Builder you'll use to script outgoing texts and define how returned texts will be parsed and responded to.


Like most Builders, the layout of the Chat Bot Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector: 


![2021-12-07_13-50-03.png](./assets_v1714/chat-bot-builder-v1714-0.png)


# Tree


Displays an expandable and collapsible breakdown of the various components that have been built out as part of an SMS experience, including each individual Chat Bot and its component Decision Menu and Text Response Capture elements. The Tree also provides the option to add additional components: clicking the '+' icon that appears when you run your mouse over a listed component provides the option to add a subcomponent that will be nested directly under said branch. 


These components and subcomponents are structured as follows:


* [**Voice Bots**](https://support.airkit.com/docs/building-a-simple-chat-bot) - typically designed around a specific work flow.
   * **[Text Response Capture](https://support.airkit.com/reference/text-response-capture-control)** - Defines three things: an outgoing text, the variable that will bind to the user's response, and the default reply. Replies are defined by denoting another Decision Menu or Text Response Capture, which the user will be directed to.
   * **[Decision Menus](https://support.airkit.com/reference/decision-menu-control) - Defines two things: an outgoing text, and ways to parse and reply to different incoming responses.** Replies are defined by denoting another Text Response Capture or Decision Menu.
      * **Decision Options** - define different ways a Chat Bot might parse and reply user input.
      * **Default Response** - defines how the Chat Bot will respond if it can't parse the reply it receives.


The Tree also enables the addition of two other components, which can nest under either Decision Menus or Text Response Capture:


* **Expression** - insert variables or other [Airscript](https://support.airkit.com/docs/airscript-quick-start) expressions into an outgoing text.
* **Web Link** - insert a link to the web portion of the [Journey](https://support.airkit.com/docs/journeys).


For a more detailed discussion on how to work with the various component parts of a Chat Bot, check out [Creating a Simple Chat Bot](https://support.airkit.com/docs/building-a-simple-chat-bot-Creating-a-Simple-Chat-Bot).


# Stage


Displays a visual representation of the various components that make up an SMS experience. Exactly what is displayed in the Stage varies to better communicate what component of the SMS experience is being examined. For instance, when examining any part of a Decision Menu, the Stage will display the outgoing text, the associated decision options, and the default response, like so: 

<img src="./assets_v1714/chat-bot-builder-v1714-1.png" alt="organizing info" style="max-width: 350px; width:100%"/>

On the other hand, when examining any part of a Text Response Capture, the Stage will display only the outgoing text and the Decision Menu or Text Response Capture that the user will be directed to once they have given a response that will be saved as the value of a variable:

<img src="./assets_v1714/chat-bot-builder-v1714-2.png" alt="organizing info" style="max-width: 400px; width:100%"/>

In both cases, outgoing or potentially outgoing texts can be edited directly in the Stage by clicking on the relevant text and making the desired edits.


For a more detailed discussion on how to work within the Chat Bot Stage, check out [Creating a Simple Chat Bot](https://support.airkit.com/docs/building-a-simple-chat-bot-Creating-a-Simple-Chat-Bot).


# Inspector


Provides the tools to examine and modify the individual elements that make up an SMS experience and configure specific interactions associated with those elements. The layout of the Inspector will vary depending on the functionality of the element being inspected.

<img src="./assets_v1714/chat-bot-builder-v1714-3.png" alt="organizing info" style="max-width: 200px; width:100%"/>


In general, there are two tabs that may appear in the Chat Bot Builder Inspector: **General** and **Actions**. (Not every element will allow you to access both tabs while being inspected, because different elements allow different modifications.)

## General

Contains the fundamental information associated with the element being inspected. For instance, if inspecting a Chat Bot, the **General** Tab will display relevant Events and variables, as well as the initial text prompt sent by the Chat Bot. If inspecting a Decision Option, the Inspector will display all potential incoming texts that the Decision Option will accept, and clicking on the '+' icon to upper right will add another.

## Actions


Under the **Actions** tab, you'll be able to access the Action Builder. This allows you to associate Action Chains with the any Events associating with the element you're inspecting.