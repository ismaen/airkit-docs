When building out forms, sometimes there is a decision that determines what data the user needs to complete. In Airkit, it is easy to dynamically hide or show content based on user interaction.


Dynamically Hiding Sections
---------------------------


Hiding and showing sections dynamically is about setting a condition on a section to determine whether or not it should appear. The visibility can be targetted to either a variable of type Boolean or a condition that evaluates to a Boolean value. There are tons of use cases for this approach: filling out forms on behalf of a minor; displaying different sections of a form based on state requirements; showing different menus based on the hour of the day at a restaurant.


Consider the following web page:


![Airhome-HideShow-FormOverview.png](./assets_v1714/hiding-and-showing-sections-of-a-form-dynamically-v1714-0.png)


Earthquake insurance is a requirement for the state of California, but is expensive and is not required everywhere. Let's make that condition optionally displayed only for the state of California.


Make sure the Label and dropdown for earthquake insurance are in their own container. Select the container, go to the *Advanced Tab* in the Inspector and enter the following into the *Is Visible* expression box:



```javascript Airscript
state = "California"
```

This assumes that the value of the dropdown for the state is set to a value of **state** on the web page. Using string comparison, it is checking that the **state** variable is equal to the text string "California" which is set by the above dropdown. Check out [Working with Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript) for more information. On the stage, the container will have a lighter opacity. This indicates that it will be conditionally visible on the state which is currently not set.


![Airhome-HideShow-Final.gif](./assets_v1714/hiding-and-showing-sections-of-a-form-dynamically-v1714-1.gif)


Notice how the Earthquake insurance only displays when "California" is selected from the State dropdown list.


Further Reading
---------------


* [Creating A Dropdown](https://support.airkit.com/docs/creating-a-dropdown) has information on how to create the dropdowns used in this example.
* [Working with Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript) is a great resource to learn about testing conditions with text in Airscript.
* [Working with Option Lists vs Dynamic Lists](https://support.airkit.com/docs/working-with-option-lists-vs-dynamic-lists) talks about how to populate dropdown lists with static or dynamic data.