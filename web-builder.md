The Web Builder provides the tools to build out the UI for web experiences, which encompass everything from the structural layout of web apps to what [Actions](https://support.airkit.com/docs/action-builder) will be taken in response to user input. This is the Builder in which [Web Flows](https://support.airkit.com/docs/web-flows) are made out of Web Pages, and where Web Pages are made out of component [Web Controls](https://support.airkit.com/reference/web-controls-overview).


Like most Builders, the layout of the Web Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector: 


![Image_12-8-21_at_10.50_AM.jpg](./assets_v1714/web-builder-v1714-0.jpg)


# Tree
----


The Tree displays, at a high level, the various individual components that make up a web experience. At any given time, the Tree can display one of two tabs: **Navigator** or **Controls**. Toggle between the two by clicking the relevant tab at the top of the Tree.


## Navigator


Displays an expandable and collapsible breakdown of the various components that have been built out as part of a web experience. 


### Web Flows


Displays and expandable and collapsible breakdown [Web Flows](https://support.airkit.com/docs/web-flows), Web Pages, and [Web Controls](https://support.airkit.com/reference/web-controls-overview-Web-Controls-Overview). This section also provides the option to add additional components: clicking the '+' icon that appears when you run your mouse over a listed component provides the option to add a subcomponent that will be nested directly under said branch. 


These components and subcomponents are structured as follows:

   * [**Web Flows**](https://support.airkit.com/docs/web-flows)- typically designed around a specific work flow.  

      * **Web Pages** - the individual pages that make up a Web Flow; users will typically only be able to see a single web page at a time.  
	
         * **[Web Controls](https://support.airkit.com/reference/web-controls-overview)** - the basic building blocks used within web pages as UI components, such as [Labels](https://support.airkit.com/reference/label-web-control), [Buttons](https://support.airkit.com/reference/button-web-control), and [Images](https://support.airkit.com/reference/image-web-control).


### Page Layouts


Where you define the global layout of an application. It can be used to [create a header or footer for web apps](https://support.airkit.com/docs/creating-an-app-header). 


### Custom Controls


Contains the tools to create [custom Web Controls](https://support.airkit.com/docs/custom-controls) that can be reused across Web Flows.


## Controls


Provides a selection of [Web Controls](https://support.airkit.com/reference/web-controls-overview) that can be dragged and dropped directly into [Web Pages](https://support.airkit.com/docs/web-flows).


Because Web Controls can only be added to Web Pages (recall how the components of web experiences are nested), the **Controls** tab is only accessible when working within a Web Page or creating a header in **Layouters**. 


# Stage
-----


Displays a visual representation of the aspect of the app being modified, making the impact of changes clear in real time. Exactly what is displayed in the Stage varies to better communicate the type of modifications being made. When examining a [Web Flow](https://support.airkit.com/docs/web-flows), the Stage will display every Web Page within it. When examining a Web Page or a [Web Control](https://support.airkit.com/reference/web-controls-overview), only that Web Page will be displayed. When the Stage displays a single Web Page, clicking on an individual Web Control within the Stage opens up the interface to make edits to it in the [Inspector](#h_01F7MC325D3N34W628TBKB9F5M). The following example shows how the interface in the Inspector changes as various Web Controls, two [Labels](https://support.airkit.com/reference/label-web-control) and a [Button](https://support.airkit.com/reference/label-web-control), are clicked on:


![2021-06-14_17-13-52__2_.gif](./assets_v1714/web-builder-v1714-1).gif)


# Inspector
---------


Provides the tools to examine and modify the individual elements that make up an application as well as configure specific interactions. Precisely what those interactions are depends which element you're inspecting. For instance, the following example shows how the Inspector can be used to modify the text that appears in a [Button](https://support.airkit.com/reference/label-web-control):


![2021-06-14_17-15-14__2_.gif](./assets_v1714/web-builder-v1714-1).gif)


To better reflect the functionality of the Inspector, its layout changes subtly even when being used to examine relatively similar things. Consider [Web Controls](https://support.airkit.com/reference/web-controls-overview): there are changes that can be made to some Web Controls but not others. For example, the Inspector appears differently when examining a [Button](https://support.airkit.com/reference/label-web-control) as compared to a [Label](https://support.airkit.com/reference/label-web-control), in part because Buttons can be clicked, [triggering actions](https://support.airkit.com/docs/action-builder), whereas Labels can't.


In general, there are three tabs that may appear in the Web Builder Inspector: *General*, *Actions*, and *Advanced*. Not every element allows access each tab while being inspected, because different elements allow different modifications.

<img src="./assets_v1714/web-builder-v1714-3.png" alt="organizing info" style="max-width: 250px; width:100%"/>

## General


Contains the fundamental information associated with the element being inspected. This includes details about the element itself, relevant variables, and material concerning [styling](https://support.airkit.com/reference/common-style-properties-of-web-controls).


## Actions


Under the *Actions* tab, you'll be able to access the [Action Builder](https://support.airkit.com/docs/action-builder). This allows you to associate Action Chains with the any Events associating with the element you're inspecting. 

## Advanced


As a rule of thumb, the *Advanced* tab provides the ability to inspect and edit any functionality that didn't fit neatly into the first two tabs. Most commonly, the *Advanced* tab is used to dictate when particular [Web Controls](https://support.airkit.com/reference/web-controls-overview) should or should not be visible or functional. For a deeper dive into how this works and when you might want to leverage this feature, check out [this document](https://support.airkit.com/docs/dynamic-forms-based-on-user-input) on creating dynamic forms based on user input.