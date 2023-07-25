The Theme Builder provides a way to make stylistic changes that apply across your entire application, ensuring consistent styling throughout each user's web Journey.


Like most Builders, the layout of the Theme Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar, to the right of which is the Stage, to the right of which is the Inspector: 


![Theme_Builder.png](./assets_v1714/theme-builder-v1714-0.png)


# Tree


The Tree is where you'll find an expandable and collapsible breakdown of the many Variants that can be edited within Theme Builder. What you select in the Tree determines what is displayed in the Stage and Inspector.

The Tree is nested as follows:

* Theme
  * Web Controls
    * Variants


## Theme


At the top level of the Tree is the Theme. You can only ever have one Theme in the Theme Builder at once, though it can be useful to name Themes when [exporting them from and importing them to](https://support.airkit.com/docs/importing-and-exporting-themes) other applications, as this can help you keep track of precisely which theme you're working with at any given time.

Working at the Theme level of the Tree also allows you to set defaults that will impact the [Variants](https://support.airkit.com/docs/styling-with-themes) of multiple [Web Controls](https://support.airkit.com/reference/web-controls-overview), such as the default color pallet and default fonts. 

<details>
  <summary>What is a Variant?</summary>

#### Variants

A Variant is a set of styling properties for a specific Web Control, similar to a class in CSS. If you're not familiar with CSS classes, you might compare Web Controls and Variants to dinnerware. Plates, cups, and forks are all like different web controls: they each have a particular function, and this is reflected in aspects of their appearance. However, not all plates look the same. A square red plate and a round blue plate are both capable of serving as plates and are simply styled differently. If you are deciding whether to set your table with your blue plates or your red plates, this is like choosing between different Variants of plates.

Every Web Control has associated Variants: cosmetic variations that appear differently but function identically. Variants can be edited in Theme Builder and then used as defaults when adding new Web Controls. For instance, within a single application, you might create two Variants of button: a rectangular one in red, and a round one in blue. Any changes made to existing Variants also apply retroactively: existing Web Controls previously styled according to the old default will immediately take the form specified by the new default. This allows for consistent branding throughout the entirety of each user's Journey, and it also makes it easy to see how different combinations of colors, fonts, and graphics look together. 

</details>

Making stylistic changes at the Theme level makes it easier to maintain consistent styling throughout your app and makes it less cumbersome to modify individual elements. The following example shows how changing the default color palette impacts Variants of multiple Web Controls at once:


![2021-06-16_15-32-43__1_.gif](./assets_v1714/theme-builder-v1714-1).gif)


## Web Controls


Nested under the Theme is every [Web Control](https://support.airkit.com/reference/web-controls-overview) that you can [style](https://support.airkit.com/reference/common-style-properties-of-web-controls). Working at the Web Control level allows you to see all Variants of that Web Control side-by-side in the Stage.


The following example shows all of the different Variants of a [Button Web Control](https://support.airkit.com/reference/button-web-control). Note that all four Variants are displayed in the Stage, while the Inspector is left blank – there are no direct changes that can be made at the Web Control level: 


![2021-06-16_15-37-56.png](./assets_v1714/theme-builder-v1714-2.png)


## Variants


Nested under the Web Controls are all the different Variants of each. Working at the Variant level allows you make stylistic changes to that Variant and see the changes as you make them.


![2021-06-16_15-51-15__1_.gif](./assets_v1714/theme-builder-v1714-3).gif)


If you want to add another Variant to a Web control, you can either duplicate an existing Variant to use as a base, or you can click on the '+' icon at the Theme level and select which Web Control you want to add a Variant to. For a more detailed dive into how to add Variants to Web Controls, check out [Adding a Variant](https://support.airkit.com/docs/working-with-themes-and-control-variants).


## Stage


The Stage displays how Variants will appear to users. Any stylistic changes you make will be reflected by what is shown on the Stage, allowing you to see the results of your changes in real time.


The following example shows how the Stage reflects changes being made to the boarder of a Button Variant in the Inspector:


![2021-06-16_15-57-24__1_.gif](./assets_v1714/theme-builder-v1714-4).gif)


### Inspector


The Inspector is where you define how Variants are styled. Exactly what styling options are available to you will depend on what you've selected in the Tree. Changes made in the Inspector will be immediately reflected in the Stage. You can also toggle over to the Web Builder to see how your changes appear as part of your broader UI. (Remember: stylistic changes made to Variants apply immediately to all instances where that Variant was used in an app.)


The following example shows what it's like to toggle from the Web Builder to the Theme Builder, make a style change – in this case, changing the font associated with the default *brandPrimaryFont* – and then see that stylistic change reflected after toggling back to the Web Builder:


![2021-06-16_16-06-44__1_.gif](./assets_v1714/theme-builder-v1714-5).gif)


For a deeper dive into the sort of stylistic changes that can be made in the Inspector, check out [Common Style Properties of Web Controls](https://support.airkit.com/reference/common-style-properties-of-web-controls).