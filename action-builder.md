The Action Builder is where you define how your app responds to triggered Events. This is done by constructing Action Chains out of individual Actions.


The Action Builder is unlike other Builders in that is it is not represented in the [Builder Bar](https://support.airkit.com/docs/builder-bar) and instead exists within the **Actions** tab of the Inspector, available only upon inspecting an element associated with an Event. For more on what Events are and what elements might be associated with them, see the documentation on [Events](doc:events).

<img src="./assets_v1714/action-builder-v1714-0.png" alt="organizing info" style="max-width: 250px; width:100%"/>

# Add Action


Clicking on the '+' icon the right of an Event in the Inspector will open the Action Menu as a popup. The left side of the Action Menu are the categories of available Actions. 

Select different categories to see the different available Actions associated; categories will appear on the right side of the Action Menu. Select an Action from the right side of the Action Menu to add it to the bottom of your Action Tree.


![2021-06-23_14-35-40__1_.gif](./assets_v1714/action-builder-v1714-1).gif)

# Action Tree


The Action Tree is where you can see all the Actions that will be performed when a particular Event is triggered. This series of Actions is called an **Action Chain**. The Actions in the Action Chain will be performed in the order they are listed. For instance, in the following example, upon clicking the relevant button, the user will [navigate to another Web Page](https://support.airkit.com/reference/navigate-to-web-page-action), and then a [Chat Bot will start](https://support.airkit.com/reference/the-start-chat-bot-action):

<img src="./assets_v1714/action-builder-v1714-2.png" alt="organizing info" style="max-width: 300px; width:100%"/>

The Action Tree can contain any number of Actions. Actions can be deleted by clicking the trash can icon to the right of the action. Actions can be re-ordered by clicking and dragging the handle at the left side of the Action. 

The Action Tree also makes it possible to define Actions that will only be taken conditionally. Actions nested under conditionals in the Action Tree will be taken only when the condition above them is met, and Actions can be dragged into and out of the umbrella of certain conditions as easily as they can be reordered.

The following example show how a simple conditional might appear in the Action Tree. In this example, a Chat Bot starts only if the variable ```session.timeZone``` is a certain value; otherwise a Voice Bot starts instead. Regardless of whether a Voice Bot or a Chat Bot starts, the user will navigate to another Web Page. Note how the Actions are nested to indicate under what conditions they'll be done:

<img src="./assets_v1714/action-builder-v1714-3.png" alt="organizing info" style="max-width: 300px; width:100%"/>


For more on working with conditionals within the Action Builder, check out [The Condition Action](https://support.airkit.com/reference/the-condition-action).


# Action Editor


Clicking on an Action in the Action Tree will open the Action Editor. This is where you'll be able to edit the configurations of the selected Action.


The editable configurations, and thus the layout of the Action Editor, will vary from Action to Action. For a more detailed dive into how each Action type can be edited, check out the reference documentation for each individual Action [here](ref:analytics-identify-action).