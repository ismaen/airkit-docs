[block:html]
{
  "html": "<iframe width=\"560\" height=\"315\" src=\"https://www.youtube.com/embed/sLqosET5IAs\" title=\"YouTube video player\" frameborder=\"0\" allow=\"accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture\" allowfullscreen></iframe>"
}
[/block]
This guide will walk through how to connect a Twilio Number to Airkit and be used as a Voice or SMS resource. This enables the ability to leverage the Voice and SMS capabilities within the platform, such as sending an SMS update to a user or having a journey get triggered by an inbound call. 

**Prerequisites:**

1.  Access to a Twilio Account
2.  Have an available number associated with the Twilio Account. See [here](https://support.twilio.com/hc/en-us/articles/223135247-How-to-Search-for-and-Buy-a-Twilio-Phone-Number-from-Console) for guidance on how to set that up.

Set up integrations in Console
------------------------------

This section will go over creating a connection to Twilio with an Airkit application.

1.  Go to [console.airkit.com](http://console.airkit.com) and click on **Integrations** > **Credentials** and then select the **+New** button to add your credentials  
 
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/connecting-your-twilio-numbers-to-airkit-v1714-0.png",
        "pasted image 0.png",
        1402,
        541,
        "#fefcfc"
      ]
    }
  ]
}
[/block]
    
2.  Name the integration and select the Twilio integration  
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/connecting-your-twilio-numbers-to-airkit-v1714-1.png",
        "pasted image 0 (1).png",
        1274,
        452,
        "#fbfbfc"
      ]
    }
  ]
}
[/block]
    
3.  The Username and Password will need to be from Twilio. On the Dashboard of a Twilio account, locate the Account SID and an Auth Token.  
      
    **Username** = Account SID  
    **Password** = Auth Token  
      
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/connecting-your-twilio-numbers-to-airkit-v1714-2.png",
        "pasted image 0 (2).png",
        1600,
        517,
        "#f7f6f6"
      ]
    }
  ]
}
[/block]
Set up phone number resource
----------------------------

This section will cover how to set up a phone number to use from your connection.

1.  In [console.airkit.com](http://console.airkit.com), click on **Resources** > then select the **+New** button.
2.  Add a name to describe the resource and click on the **Capabilities** dropdown and select **Send Text Message** to set up a chat bot. To set up a Voice Bot, select **Send Voice**.  
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/connecting-your-twilio-numbers-to-airkit-v1714-3.png",
        "pasted image 0 (3).png",
        1418,
        504,
        "#faf8f9"
      ]
    }
  ]
}
[/block]
      
    
3.  Select your **datasource** that was created in the previous step. Under **Remote ID**, select a phone number that is available.

Set up SMS resource in your app - Configuration Builder
-------------------------------------------------------

In this section, we will set up the Phone number to be used via SMS.

1.  In the app, click on **Configuration builder** and scroll down to **Chat Bot.** Then select the SMS Resource that was created in the previous step. It should show up as the name previously provided.  

[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/connecting-your-twilio-numbers-to-airkit-v1714-4.png",
        "pasted image 0 (4).png",
        1384,
        473,
        "#fcfbfb"
      ]
    }
  ]
}
[/block]
    
2.  Once selected, the app will now send SMS through the number provided!
    

Set up Voice resource in your app - Configuration Builder
---------------------------------------------------------

This section will cover how to set up a phone number to be used via voice

1.  In the app, click on **Configuration builder** and scroll down to **Voice Bot.** Then select the Voice Resource that was created in the previous step. It should show up as the name previously provided.  
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/connecting-your-twilio-numbers-to-airkit-v1714-5.png",
        "pasted image 0 (5).png",
        1336,
        457,
        "#fcfbfb"
      ]
    }
  ]
}
[/block]
    

2.  Once selected, the voice resource will use the Twilio integration!
    *   **Voice Locked Behavior:** What action to take if someone calls in with the same number with a live session.
    *   **Incoming Call Launch Behavior:** What action to take if the phone number receives an incoming call.

Next Steps
---------------

Once the Twilio account is connected, it can then be used to integrate with the chat bots and voice bots in **Web Builder**. Also, when dealing with phone numbers in your app, it is best practice to use the [FORMAT_PHONE](ref:format_phone) function to ensure the phone number gets passed with the region correctly. For more information on how how to leverage the associated phone number, see some of the topics below: