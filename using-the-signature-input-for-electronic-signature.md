Airkit makes it possible to collect a user's signature with the Signature Input. These signatures can be used where a user's signature is required, such as legal documents. For example, signing a housing lease contract or a work order. 

Configuring the Signature Input
-------------------------------


The Signature input is under the Input section in the Add Control Dialog:


![AirHome-Signature-AddControl.png](./assets_v1714/using-the-signature-input-for-electronic-signature-v1714-0.png)


The signature input is a complex control that contains a place to draw the signature, clear the box, and save the drawn signature. By default, it is set up only for drawing a signature, but there is an option to set up a typed signature as well.


On the page with the signature control, add an Asset Variable named **signature**, a text variable named **typed_signature**, and another text variable named **mode**. Select the Signature control, click the + button to the right to add a Text Input. This will be for the text option.


In the Inspector, set the value to **signature**. This is an asset variable where the saved image of the drawn signature will be stored. Set the *Init Mode* to draw. This tells the control to start out expecting to received drawn input. The user can switch to text. Set the Signature value to **typed_signature**. This is the text variable where the typed value will be stored.


Under the style section, expand the *Signature Input Variant* to see the stylable parts of the component. Selecting pad, for example, style the actual drawing surface.


Select the Actions Tab in the Inspector. Add a [Set Variable](https://support.airkit.com/reference/the-set-variable-action) action and set the value of **activity.mode**to **event.mode**. This is setting the mode value to either "draw" or "type." Select the typed_signature input and under the Advanced Tab in the inspector, set the *Is Visible* value to:



```javascript Airscript
activity.mode = "type"
```

This checks the current value of the mode for the signature mode and only displays the text input if the value is set to type.


![AirHome-Signature-Sign.png](https://a01-support.airkit.com/using-the-signature-input-for-electronic-signature/AirHome-Signature-Sign.png)


Getting the signature graphic
-----------------------------


Once the user clicks *Save* on the signature in draw mode, the signature is saved to the asset associated with the value of the signature pad. The save is not instantaneous but occurs pretty quickly. Once the save has been made, the asset will hold a pointer to the asset that is associated with the signed signature. See the [Asset Documentation](https://support.airkit.com/reference/the-asset-data-type) for information about each of the properties on the asset object.


To create a confirmation page on the lease signing, let's create another card. Copy the contract from the signature page and include an [image web control](https://support.airkit.com/reference/image-web-control). In the inspector set the URL to:



```javascript Airscript
ASSET_TO_URI(  
  signature  
)
```

[ASSET_TO_URI](https://support.airkit.com/reference/asset_to_uri)() gives an accessible URI for the asset provided. This will set the image URL to a valid URI that can be rendered on the web page. In addition to being rendered on screen, signatures can be attached to PDFs in Data Flows, or used anywhere else an asset may be used.


Further Reading
---------------


* [The Asset Data Type](https://support.airkit.com/reference/the-asset-data-type) has more information on the properties of an asset.
* [Introduction to Data Flows](https://support.airkit.com/docs/data-flows) has information on how to remit information like signatures.