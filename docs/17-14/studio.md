Airkit Studio is the interface in which your Airkit apps can be created and edited. This article goes over the basic structure of the Studio, as well as the placement and functionality of some important buttons located at the top and leftmost side of the interface.


![2021-05-25_15-14-44.png](./assets_v1714/studio-v1714-0.png)


# General Structure


## [Builder Bar](https://support.airkit.com/docs/builder-bar)


The Builder Bar provides a way to toggle between Airkit's many Builders, the interfaces that allow you to construct and edit different components of your apps.


**Example**: When you first create a new Airkit app, you're taken to the [Journey Builder](https://support.airkit.com/docs/journey-builder) by default. The Journey Builder provides a big-picture view of how the component pieces of your application fit together; it is a particularly good place to start if you want to lay a foundation for you app using [Kitcloud](https://support.airkit.com/docs/kitcloud) templates. Once you've laid out the big-picture structure of your app, you want to make a small tweak to the UI. This (along with all other specific user interactions) is the domain of the [Web Builder](https://support.airkit.com/docs/web-builder) – the bird's-eye view of Journey Builder does not lend itself to detailed editing – so you click on the Web Builder icon within the Builder Bar and move to the Web Builder.


## Tree


The Tree, if applicable, is where you'll find an expandable and collapsible breakdown of the components examinable within the Builder. The Tree is a part of the Builder: different Trees belong to different Builders, and you can remind yourself which Builder you're working in at any given time by looking at which Builder icon is highlighted in pink on the Builder Bar.


Not all Builders have a Tree; the [Configuration Builder](https://support.airkit.com/docs/configuration-builder) and [Media Library](https://support.airkit.com/docs/media-library), for instance, do not have Trees because their components do not nest.


**Example:** In the [Web Builder](https://support.airkit.com/docs/web-builder), **Navigator** tab within the Tree contains three main sections: **Web Flows**, **Page Layouts**, and **Custom Controls**. You want to make a small tweak to the UI of one of your web pages, so you expand the *Web Flow* section. This provides a list of the [Web Flows](https://support.airkit.com/docs/web-flows) that make up your web application, and you can expand each Web Flow to access particular Web Pages. From there, you can inspect individual [Web Controls](https://support.airkit.com/reference/web-controls-overview). Still working within the Tree, you click on the specific Web Control you want to edit; all editable properties of that Web Control appear in the Inspector (see below).


## Stage


The Stage displays a visual representation of the aspect of the app you're modifying, allowing you to see the results of your changes in real time. Exactly what is displayed in the Stage varies from Builder to Builder, to better communicate the type of modifications each Builder facilitates.


**Example:** As you use the [Web Builder](https://support.airkit.com/docs/web-builder) to edit the UI of your web app, the Stage showcases what those changes will look like to the end user. You can also click on a [Web Control](https://support.airkit.com/reference/web-controls-overview) as it's displayed in the Stage in order to open up the interface to make edits to it in the Inspector (see below). To change the color of a particular [Button](ref:button-web-control), you click on said Button as it appears in the Stage, then make your desired stylistic changes. You can see the changes as you make them, so if you find your initial changes clash with the UI of the broader Web Page, you can iterate until you find a look you love.


## Inspector


The Inspector is where you can examine and modify individual elements pertinent to a Builder. Like the Tree, the Inspector is a part of the Builder: different Inspectors belong to different Builders, and you can remind yourself which Builder you're working in at any given time by looking at which Builder icon is highlighted in pink on the Builder Bar. However, unlike the Tree, the display in the Inspector does not remain consistent as long as you are working within the same Builder; the information within the inspector – and even the format through which that information is presented – varies depending on what element is being inspected.


Not all Builders have an Inspector; the [Configuration Builder](https://support.airkit.com/docs/configuration-builder) and [Media Library](https://support.airkit.com/docs/media-library), for instance, do not have Inspectors because all relevant information is displayed and editable within the Stage.


**Example:** You're using the Inspector to examine a particular [Button](ref:button-web-control). To make a stylistic change to the Button, you go to the **General** tab and expand the contents under **Style**. You want to change the background color of the button, so you expand the contents under **Background**. The dropdown menu that appears allows you to to modify the color of the button, or even use a picture to fill in the button's background.


# Key Buttons in the Studio


While there are many different buttons associated with the different Builders, as well as their Trees and Inspectors, there are a few buttons in the Studio that will always be available to you. These are located at the top of the Studio interface, as well as in the Builder Bar.


## Builders in the Builder Bar


No matter what Builder you're working within, you'll aways have access to the same Builder Bar, which is what allows you to toggle between different Builders while working on your app. For a more detailed discussion on what each Builder is, check out [documentation on the Builder Bar](https://support.airkit.com/docs/builder-bar).


## [App Preview](https://support.airkit.com/docs/app-preview)


The App Preview button allows you to run and test your Airkit apps without needing to publish them. By emulating a user's [Journey](doc:journeys) through your app, you can check to make sure everything functions as intended. 


## Return to Console


This button takes you back to the [Console](https://support.airkit.com/docs/console), where, among other things, you can access every application you have saved within your [Organization](https://support.airkit.com/docs/airkit-organizations).


## Publish


Click on the Publish Button when you want to [publish your app](https://support.airkit.com/docs/publishing-your-application).


## Save


Save your work frequently, so you don't have to worry about losing progress by accident! In lieu of clicking the **Save** button, the usual keyboard shortcuts also work: CMD + S or CTRL + S will save your work equally well.


## Undo


Airkit's **Undo** button functions like every other Undo button: if you make a change you don't want to keep, press the **Undo** button to undo the last thing you did.


## Redo


Airkit's **Redo** button functions like every other Redo button: if you pressed the Undo button and don't like the results, use the **Redo** button to redo what you undid.