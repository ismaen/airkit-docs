Connecting and configuring resources
-------------------------------

There are different types of Resources you can add to your Org's Console that will allow you to unlock more functionality for your apps and give them a personalized touch. 

In the **Console** menu, go to **Resources > All Resources** to see a list of the enabled resources and, for instance, manage your available phone numbers.
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/adding-and-modifying-resources-v1714-0.png",
        "AllResources.png",
        1230,
        441,
        "#fcfbfb"
      ]
    }
  ]
}
[/block]
Adding Resources
----------------

To add a new Resource, click on **Create new** at the top right corner. Enter a name for it and select its type of capability. 
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/adding-and-modifying-resources-v1714-1.png",
        "CreateNew.png",
        530,
        518,
        "#fbf9fa"
      ],
      "sizing": "smart"
    }
  ]
}
[/block]
It will then show up both in the **All Resources** list and in the list corresponding to the type of Resource.

There are three types of Resources:

###Phone Numbers

They have the following capabilities:

* **Send Voice:** allows to send and receive voice messages and commands and it's used in conjunction with Voice Bots.
* **Send Text Message:** allows to send and receive text messages and it's used in conjunction with Chat Bots.

###Domains

They have the following capabilities:

* ** URL Domain:** registers a custom domain after DNS registration.
* ** URL Route:** registers a URL path with a unique key, for example, for an API endpoint.
* ** Email Domain:** registers a custom domain to be used for outbound email addresses.
* ** Email Address:** validates a specific email address to be used from the app, for example, as a sender.

###Embeds

Retrieve a customizable JSON code to insert your app into other webpages.

Configuring the Resources in the application
----------------

The **Resources** that you set up in the **Console** are ready to be added to your apps from **Configuration Builder**.

In **Voice Bot** or **Chat Bot**, pick the **Phone Number** you entered as a **Resource** to send voice or text messages from your app, you can even use this action to create a new Journey.

[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/adding-and-modifying-resources-v1714-2.png",
        "ConfiBuilder1.png",
        1162,
        572,
        "#fdfcfd"
      ]
    }
  ]
}
[/block]
In **Email**, you can add the registered **Email Domain** or add a validated outbound **Email Address** to, for example, send notifications to end users. 
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/adding-and-modifying-resources-v1714-3.png",
        "ConfigBuilder2.png",
        973,
        411,
        "#fdfdfd"
      ]
    }
  ]
}
[/block]
In **Integrations**, **Journey Links**, **Web URLs**, and **Portal Link**, you’ll find the **URL Route** you included as a resource available for different purposes.

For example, in **Web URLs** you can add the **URL Route** to launch the application and start the Airkit experience.

[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/adding-and-modifying-resources-v1714-4.png",
        "ConfigBuilder3.png",
        948,
        301,
        "#fdfdfd"
      ]
    }
  ]
}
[/block]