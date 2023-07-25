## Embed your app on any webpage

Airkit embeds provide yet another way to make your apps available to your customer. Embedding helps provide your apps directly inside your existing web pages, allowing your customers to interact with your apps without ever leaving your page.

## Creating an embed

![embeds1.gif](./assets_v1714/embeds-v1714-0.gif)

Clicking on the embed option under resources shows you your full list of embeds, and allows you to add new embeds. Click on an embed will give you the capability of making updates to your embed. After providing a name for the embed, selecting the App, and selecting the Deployment, additional options are available to configure different aspects of the look, feel, and functionality of the embed. Here is a list of configurable options:

- Target Hostnames → A list of all the Hostnames where this embed could be activated from.
- Use Launcher → Shows the launcher on your page. Turning this off will mean that a custom iFrame will need to be configured on your page.
- Show Launcher on Load → Turns on the capability to auto show the launcher. Turning this off will hide the launcher until manually shown - via JavaScript method call.
- Show Frame on Load → Configures whether we should automatically pop the frame and show the experience. Turning this off will mean that - the user has to click the launcher before seeing the iFrame.
- Remember Journey → Allows for the Journey state to be maintained. This can be helpful to prevent the Journey from disappearing during - refresh or if you have the embed on multiple web pages.
- Wait for Journey → Turns on the ability for the embed to wait until a journey has been found. This can be helpful if the journey is - started via another channel.
- Show Frame on Load After Duration → This will show the frame after a specific amount of time has passed.
- Show Hint on Load After Duration → Shows a hint on the launcher after specific amount of time. This hint can be helpful in directing the - users attention to the embed launcher.
- Hide Hint after Duration → Hides a hint after a specific amount of time.
- Styles → Allows you to configure the size of the frame, the size of the launcher, and additional theming properties associated with the embed.

## Adding an embed to your webpage

To add an embed to your webpage, you’ll need to add the following javascript to your site.

```javascript JavaScript
<!--  Start a New Session -->

<script src="https://client.airkit.com/17/air-client.js"></script>
<script>
    Airkit.createClient("EMBED_ID").then((client) => client.start())
</script>
```



**Note** the '17' within the URL refers to the Airkit Runtime version. 

This snippet will start a new Airkit journey whenever a person visits this page. The properties you selected on the embed will define the exact launch behavior. For more detailed information, please reach out to our support team and we can provide you additional details.