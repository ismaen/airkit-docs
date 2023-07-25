Themes within Airkit provide a way to brand an application to create a particular look and feel.  There's the ability to import/export themes, change the visual properties of any type of controls, or add specific variants for each control, all configured within [Theme Builder](https://support.airkit.com/docs/theme-builder). This article will cover the following topics:


* [Variants](#h_01F38GA75JVBN2C45Q89CNDVBF)
* [Modifying a Variant](#h_01F38GAE603BQD05H95VRZRRN8)
* [Adding a Variant](#h_01F38GAMNFSJPAK687KYZA630T)
* [Changing Styles in a Theme](#h_01F38GAVRX68Y1B16BM3VMKHRH)
* [Adding a Style Class to a Theme](#h_01F38GB49QCPS4HEF27ZJKSN7M)


![Screen_Shot_2021-04-13_at_1.38.27_PM.png](./assets_v1714/working-with-themes-and-control-variants-v1714-0.png)


Variants
--------


A variant in Airkit is a set of styling properties for a specific control, similar to a class in CSS. Variants are used to create style uniformity across an application. For example, labels have multiple variants such as a body text variant or a headline variant, and these variants can be selected when adding a label control to an application. Each of these variants have different properties associated with them and can be maintained and edited within Theme Builder. When a variant is edited, then that change will reflect across all instances of that control using that variant. Variants are also seen when adding a control in an application. When adding a control, there is the option to select the different variants available with the option to modify it later as well.


![mceclip0.png](./assets_v1714/working-with-themes-and-control-variants-v1714-1.png)


Modifying a Variant
-------------------


For example, an application uses a mix of body text and headline text and there is a requirement to change all the headline text to have a bold font weight. Instead of identifying all of the label controls with a headline text and overriding the styles, the headline text variant can be edited. 


Go to Theme Builder and open the **Label Variant** accordion in the tree. Select **largeHeadline**, which is the largeHeadline variant that would be used across the application. 


![mceclip0.png](./assets_v1714/working-with-themes-and-control-variants-v1714-2).png)


When **largeHeadline** is selected, the inspector will show all of the style properties that are associated with **largeHeadline**. Any changes made here will reflect across all instances of largeHeadline in an application, unless the styles are overrode in Web Builder. To change the font weight of the largeHeadline to bold, change the dropdown from Regular to Bold under the Font properties. 


![mceclip1.png](./assets_v1714/working-with-themes-and-control-variants-v1714-3.png)


After saving, the changes will then reflect in the application. 


Adding a Variant
----------------


If none of the variants that come default fit the need of an application or the application requires additional variants, there is the ability to add a variant to any of the controls. This example will show how to add a Button Variant.


Go to Theme Builder and click on the '+' icon at the Theme level in the tree. Select '**Button**'. 


![mceclip2.png](./assets_v1714/working-with-themes-and-control-variants-v1714-4.png)


Select the 'Button Variant' accordion in the tree and there will be a variant called 'default 2' which was the variant just added. The variant can also be renamed to a name that is more fitting for that variant. 


![mceclip3.png](./assets_v1714/working-with-themes-and-control-variants-v1714-5.png)


Select 'default 2' and see the inspector. In the inspector is where the different style properties can be set. Once the styles are set, save the application and the variant can be used throughout the application. 


There is also the ability to duplicate variants as well. To duplicate variants, click on the 'Duplicate' icon to make an exact copy of the selected variant.


![mceclip1.png](./assets_v1714/working-with-themes-and-control-variants-v1714-6).png)


Changing Styles in a Theme
--------------------------


In Theme Builder, there are different levels at which styles can be applied. Styles can be applied by variant or they can be applied to affect the entire application. Themes consist of Colors, Sizes, and Fonts and include theme variables that can be referenced throughout the application and control variants. These styles are also used by all the default variants as well, so when configured, it will also affect the default variants. 


To change a style in a Theme, go to Theme Builder and click on '**Theme'** in the tree. The inspector will then show all of the different theme variables that can be configured. 


![mceclip4.png](./assets_v1714/working-with-themes-and-control-variants-v1714-7.png)


Then select a property to change. For example, to change the primary color of the brand of an application, click on the hex value of the **brandPrimary** property and change the color. This change will automatically affect all controls and variants that use the brandPrimary property for that control. 


![mceclip5.png](./assets_v1714/working-with-themes-and-control-variants-v1714-8.png)


Changing style properties at the Theme level is useful for creating a stylesheet for an application without having to change colors, fonts, or sizes in many areas. 


Adding a Theme Variable
-----------------------


If a theme requires additional styles, there is also the ability to add additional color, size, or font theme variables. To add a Theme Variable, go the Theme Builder and with **Theme** selected in the tree, click on the '+' icon next to one of the Theme properties. This will create a new Color, Size, or Font variable to be used across the application or variants. 


![mceclip6.png](./assets_v1714/working-with-themes-and-control-variants-v1714-9.png)


Further Reading
---------------


Themes and control variants provide a mechanism to quickly and efficiently style an application. They help bring a uniform look and feel to applications and help standardize how the different controls look across the application. For more information on styling, see:


* [Common Style Properties of Web Controls](https://support.airkit.com/reference/common-style-properties-of-web-controls)
* [Working with Custom Fonts](https://support.airkit.com/docs/working-with-custom-fonts)
* [Importing and Exporting Themes](https://support.airkit.com/docs/importing-and-exporting-themes)