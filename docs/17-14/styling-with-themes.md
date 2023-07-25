The [Theme Builder](https://support.airkit.com/docs/theme-builder) provides a way to make stylistic changes that apply across your entire application. This allows for consistent styling throughout a web app, and it also makes it easy to see how different combinations of styling components look when used together. In this document, we'll discuss: 


* [What does the Theme Builder do?](#h_01F8DWQQW7AEHHABDVMMSX3KJE)
* [What is a Variant?](#h_01F8DWQWB285CP2XQ7D5KR2ZZM)
* [When to use the Theme Builder](#h_01F8BBZKH1J19YWNG4HH3KX80B)
* [Applying Themes to multiple apps](#h_01F8BBZW1KT96ZBCE8X8S16G4T)


### What does the Theme Builder do?


In Airkit, web apps are made out of component parts called [Web Controls](https://support.airkit.com/reference/web-controls-overview), and each Web Control has visual properties, including (just to name a few) size, position, and padding. In the Theme Builder, you can set customized defaults for these properties, and any changes you make will apply both to any future instances where those Web Controls are added as well as retroactively: existing Web Controls previously styled according to the old default will immediately take the form specified by the new default. Setting customized defaults is done by defining [Variants](https://support.airkit.com/docs/working-with-themes-and-control-variants). 




<div class="row">
  <div class="column" style = "padding:5px">
<img src="./assets_v1714/styling-with-themes-v1714-0.png" alt="organizing info" style="max-height:350px"/>
</div>
 <div class="column" style = "padding:5px">
<img src="./assets_v1714/styling-with-themes-v1714-1.png" alt="organizing info" style="max-height:350px"/>
</div>
 <div class="column" style = "padding:5px">
<img src="./assets_v1714/styling-with-themes-v1714-2.png" alt="organizing info" style="max-height:350px"/>
</div>
</div>





### What is a Variant?


A [Variant](https://support.airkit.com/docs/working-with-themes-and-control-variants) is a set of [styling](https://support.airkit.com/reference/common-style-properties-of-web-controls) properties for a specific [Web Control](https://support.airkit.com/reference/web-controls-overview), similar to a class in CSS. 


If you're not familiar with CSS classes, you might compare Web Controls and Variants to dinnerware. Plates, cups, and forks are all like different web controls: they each have a particular function and this is reflected in aspects of their appearance. However, not all plates look the same. A square red plate and a round blue plate are both capable of serving as plates, but are simply styled differently. If you are deciding whether to set your table with your blue plates or your red plates, this is like choosing between different Variants of plates.


As the above comparison implies, a single Web Control might have multiple Variants. For example, out of the box, the [Button Web Control](https://support.airkit.com/reference/button-web-control) comes with four Variants: *default*, *buttonSecondary*, *buttonText*, and *link*. All of these Button Variants behave in the same way, but they look different from each other. When adding a Button to a Web Page or modifying a Button already present, you have the option to choose or change what Variant dictates the Button's appearance. The following example shows what it looks like to cycle through different Button Variants in the [Web Builder](https://support.airkit.com/docs/web-builder):


![2021-06-16_15-12-32__1_.gif](./assets_v1714/styling-with-themes-v1714-3).gif)


### When to use the Theme Builder


Use the Theme Builder when you want to make [stylistic](https://support.airkit.com/reference/common-style-properties-of-web-controls) changes that apply throughout your whole application, or when you want to create re-usable [Variants](https://support.airkit.com/docs/working-with-themes-and-control-variants) that you can easily and repeatedly access while designing the UI for a web app. If you want to keep your styling consistent throughout an application, you'll be making most, if not all, of your stylistic changes in the Theme Builder.


The [Web Builder](https://support.airkit.com/docs/web-builder) also provides the tools to [style](https://support.airkit.com/reference/common-style-properties-of-web-controls) [Web Controls](https://support.airkit.com/reference/web-controls-overview), but only individual Web Controls that have already been added to a web app. If the goal is to create an element that looks completely unique – and is thus styled in a way you won't ever want to reuse – you can make stylistic changes to that particular element directly in the Web Builder.


It is technically possible to make all stylistic changes in the Web Builder. This approach, however, will quickly become cumbersome and repetitive, and it is not recommended.


### Applying Themes to multiple apps


Once you've finalized a theme, either by experimentation or by copying an existing style guide, you can apply it to other apps simply by saving it as a JSON and uploading it into another app's Theme Builder. This allows you to automatically apply styling conventions that are both standardized and customized to all of your apps.


For a more detailed walkthrough of how save and re-use Themes, check out [Importing and Exporting Themes](https://support.airkit.com/docs/importing-and-exporting-themes).


### Further Reading


* [Theme Builder](https://support.airkit.com/docs/theme-builder) - Explore the layout and functionality of Theme Builder
* [Working with Themes and Control Variants](https://support.airkit.com/docs/working-with-themes-and-control-variants) - Get into the nuts and bolts of how to make the most of Theme Builder.
* [Common Style Properties of Web Controls](https://support.airkit.com/reference/common-style-properties-of-web-controls) - Dive into the stylistic changes you can make to your Web Controls.