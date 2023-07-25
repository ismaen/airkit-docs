Airkit comes with fonts out of the box, [Google Fonts](https://fonts.google.com/), as well as the ability to upload custom fonts. Custom fonts are great for matching fonts in an application to exactly match a style or brand. 


Airkit will accept the following font types: 


* .otf
* .ttf
* .woff
* .woff2


Adding a Custom Font
--------------------


To add a custom font, go to [Media Library](https://support.airkit.com/docs/working-with-files-and-media) in the Builder Bar and click on the **Upload** button. Upload the font to be used in the application. 


![mceclip0.png](./assets_v1714/working-with-custom-fonts-v1714-0.png)


The Font will be added as an asset to the Media Library and can now be used as a Font style.


![mceclip1.png](./assets_v1714/working-with-custom-fonts-v1714-1.png)


Changing the Primary Font Across an Application
-----------------------------------------------


Fonts can be easily changed across an application by changing the primary font at the Theme level. To change the primary font, go to Theme Builder and select '**Theme**' in the tree.  


![mceclip2.png](./assets_v1714/working-with-custom-fonts-v1714-2.png)


Then go to the Inspector and expand the Fonts accordion. To change the primary font, click on the font name next to brandPrimaryFont and select the **Custom Font** tab. Select the font to be used, and click on **Save**. Any Google Font can also be used here as well. 


![customfonts__1_.gif](./assets_v1714/working-with-custom-fonts-v1714-3).gif)


Now all labels or text that is using the brandPrimaryFont variable will use the new custom font that was selected.


Additionally, to add a secondary font variable that can be used across the application, click on the '**+**' icon next to Fonts and add another variable name with an associated font. This is useful if the application required a completely different font for certain areas or flows of the application. 


![mceclip4.png](./assets_v1714/working-with-custom-fonts-v1714-4.png)


Further Reading
---------------


Custom fonts are just one of the many styling tools to help build out applications to match a specific brand or look and feel. To dive deeper into topics related to styling see:


* [Working with Themes & Control Variants](https://support.airkit.com/docs/working-with-themes-and-control-variants)
* [Common Style Properties of Web Controls](https://support.airkit.com/reference/common-style-properties-of-web-controls)