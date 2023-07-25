In the Studio and throughout your app, there are various different namespaces or scopes. This is a way of qualifying access to particular variables throughout your experience. The general best practice is to restrict your variable to least level of access you need in order to make your experience work. We will talk more about that below.


Some namespaces are editable and others are set at the beginning of the experience and cannot be modified.


# High-Level Scopes


On each Journey there are some high-level scopes:


* Session - Contains start parameters and session level variables.
* Profile - contains profile level configuration variables.
* Theme - contains theme level configuration.
* Activities - contains a list of all loaded activities.
* ActivityGroups - contains a list of all loaded activity groups.
* Configuration - Contains app specific configuration values.


Many of these high-level scopes are used for app configuration and not really meant to be modified within your experience. The one main exception is Session where we can store variables that are able to accessed on any Web Flow, Web Page, Chat Bot, Voice Bot, or Event.


*Note: While both Configuration and Profile scopes are modified in the Configuration Builder, the Configuration scope contains information about resources while Profile contains variables at the profile-level.*


# Defining Session-Level Variables

In the context of Airkit apps, the terms Session and Journey are interchangeable. Session- or Journey-level variables are set in the Journey Builder. If you don’t see the Journey section on the right click anywhere on the stage.


![1134624816.png](./assets_v1714/variable-scopes-v1714-0.png)


Under **variables** you can click the '+' icon and add session-level variables. These variables will be available most places throughout the app, but remember they are not accessible within Connection Builder – you would need to pass them into a connection.


# Working With Scopes Within Your Web Flows


When working within your Web Flows and Web Pages, you might want to create variables to store values throughout your application. In general, the flow of the variable scoping looks like this:


* Session (Journey) - accessible Everywhere.

  * Activity Group (Web Flows/Chat Bots/Voice Bots)- accessible to all activities within the activity group.

    * Activity (Web Pages/Decision Menus) - accessible only on the on the current activity.


![1134854182.png](./assets_v1714/variable-scopes-v1714-1.png)


As mentioned above, the general best practice is to try to store you variables at the lowest scope. This will ensure the highest level of reusability of your activities and activity groups.

See [documentation on Data Types](ref:data-types-overview)] for information selecting variable type.


To access a variable in a particular scope, for example in creating the text for a label, you put in the ```scope.variableName``` in the expression editor.


![1134821430.png](./assets_v1714/variable-scopes-v1714-2.png)


# Working With Scope Within Events


Events have their own scope as they do not exist within the context of a particular activity. You can set variables on Events by selecting the **Event Source** in Journey Builder and adding variables. When you fire an event you can pass in values to the variable.


![1134788654.png](./assets_v1714/variable-scopes-v1714-3.png)


from within the event, you can then reference that value as ```event.foo``` and get the value passed in.


# Working With Scopes Within Custom Controls


When building custom controls, you are able to define what inputs or data is available to the control. During the design of your custom control, any defined inputs will be available on the **control** namespace. For example, if your custom control has an input named ```title``` , then ```control.title``` is how you’d reference that variable within the control.


As you implement your custom control, you can pull variables from the **session**, **activityGroup**, or **activity** contexts.


# Working With Scopes Within Connections


Connections exist as independent steps. They have access to all the inputs passed in but do not have access to things like **session**, even if they are run from a session. Also, future data operations have access to all the outputs created by previous data operations. This means that if you create a transform in the first step. You can still access the return value of that transform in the 5th step without having to do anything special.


# Profile Variables


Your app can contain different profiles. Each profile has a unique set of values and resources associated with them. Talking about profiles in general is a whole different topic, but let's talk about how to create a profile-level variable and modify it.


Go to Journey Builder and start like you would be creating a session-level variable.

Once you have the variable created, right click on it. Select **Convert To Setting** from the dropdown.


![1131675713.png](./assets_v1714/variable-scopes-v1714-4.png)


The little symbol next to the variable name indicates that it is a profile level-variable. Once you’ve set it to a profile variable, we can adjust the value of the profile variable in Configuration Builder. Scroll down the bottom until you see **App Settings**, you can insert a value in the value section.

<img src="./assets_v1714/variable-scopes-v1714-5.png" alt="organizing info" style="max-width: 300px; width:100%"/>

You can change the value of ```configVar``` for each different app profile. You can then use this variable throughout your cards as ```profile.configVar```. Profile variables have the same access restrictions as session-level variables.

![1131642953.png](./assets_v1714/variable-scopes-v1714-6.png)