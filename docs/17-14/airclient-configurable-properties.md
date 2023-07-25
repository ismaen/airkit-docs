Use the Console to create a new Embed. Embeds are tied to a deployment of an App. This article will cover the details associated with creating an Airkit Embed in detail.

## Basic Configuration

### Name

A simple text string to denote the Embed. Can include spaces.

### App

Selecting the Application that has the deployment to use.

### Deployment

The deployment key of the app to embed.

### Target Hostnames

This is a security measure to determine the valid places to embed the application from.

- **protocol://hostname**- Generic way to define any protocol and hostname, for example, "<http://airkit.com.>"
- **https\://** - Allows hosting on any secure https connection.
- **http\://** - Allows embedding on any unsecured http connection.
- **file://**- Allows for locally hosted files to embed the application.

It is possible to specify one or more of these specifications. This is a great way to restrict where an embed may be displayed for security. 

## Options

### Use Launcher

Shows the launcher on your page. Turning this off will mean that a custom iFrame will need to be configured on your page.

### Show Launcher on Load

Turns on the capability to auto show the launcher. Turning this off will hide the launcher until manually shown - via a JavaScript method call.

To launch within a custom iFrame, create the iFrame and then pass it to client create:

```javascript JavaScript
Airkit.createClient("EMBED_ID", <<iframe>>, configObject?, hosts?)
```



The **EMBED_ID** comes from the client created. The **configObject** matches the [Configuration Object](https://support.airkit.com/docs/airclient-configurable-properties#configuration-object) properties. The **hosts** follow the [Host Object.](https://support.airkit.com/docs/airclient-configurable-properties#host-object)

### Show Frame on Load

Configures whether we should automatically pop the frame and show the experience. Turning this off will mean that - the user has to click the launcher before seeing the iFrame.

### Remember Journey

Allows for the Journey state to be maintained. This can be helpful to prevent the Journey from disappearing during a refresh or if you have the embed on multiple web pages.

### Wait for Journey

Turns on the ability for the embed to wait until a journey has been found. This can be helpful if the journey is - started via another channel.

### Show Frame on Load After Duration

This will show the frame after a specific amount of time has passed in milliseconds.

### Show Hint on Load After Duration

Shows a hint on the launcher after a specific amount of time in milliseconds. This hint can be helpful in directing the user's attention to the embed launcher.

### Hide Hint after Duration

Hides a hint after a specific amount of time in milliseconds.

## Styles

The styles section is a configuration block for the appearance of the Embed.

### Size Properties

There are four properties at top of the section that is related to the width and height of the embed.

- **formWidth** - this is the width of the displayed, presented embed.
- **formHeight** - this is the height of the displayed, presented embed.
- **promptWidth** - this is the width of the prompt if one is configured and time is set for it to be displayed.
- **promptHieght** - this is the height of the prompt if one is configured and time is set for it to be displayed.

These properties are defined in CSS width, so **px, rem, em**, etc are valid.

### Container

The container is the parent container of the entire Embed visible area. Styles on this block are used to determine the layout of the base object.

### Frame

The frame is the external container of the app. It is independent of the button. It will contain the actual app of the embed.

### Form

The form is nested within the container, within the frame. This is the direct parent of the app. 

### Button

These properties relate to the button to launch the embed. It is a collection of CSS properties that will be added to the button on the page.

### Button Image

The button image is contained within the button. These properties relate to the source image of the button. The **src** property is set to _null_ by default. Put in a fully qualified URL for the image. Width and Height are the size of the image to be displayed.

### Hover

The hover is a pre-prompt for the embed. This is the outer container of the hover. 

### Hover Title

The hover title is the title box on the hover displaying the title message. The **text** property will be used as the header of the hover box.

### Hover Body

This is the body text of the hover. The **text** property and the color of the text to be displayed within the hover.

## Adding an embed to your webpage

To add an embed to your webpage, you’ll need to add the following javascript to your site.

```javascript JavaScript
<!--  Start a New Session -->

<script src="https://client.airkit.com/17/air-client.js"></script>  
<script>  
    Airkit.createClient("EMBED_ID").then((client) => {  
      client.start()  
    })  
</script>

```



This snippet will start a new Airkit journey whenever a person visits this page. The properties you selected on the embed will define the exact launch behavior. To get the correct version of the **EMBED_ID**, select the embed in Console and click the file icon in the Embed Script column. This will copy the appropriate embed code to past into HTML.

### Configuration Object

A configuration object is an object that can be passed to **Airkit.createClient()** when using a custom iFrame. The properties in the object match those defined above.

```
interface EmbedConfig {  
  useLauncher?: boolean  
  showLauncherOnLoad?: boolean  
  showFrameOnLoad?: boolean  
  showFrameOnLoadAfterDuration?: number  
  showHintOnLoadAfterDuration?: number  
  hideHintAfterDuration?: number  
  rememberSession?: boolean  
  waitForSession?: boolean  
  style?: any  
}
```



### Host Object

Host object is the last property passed to the **Airkit.createClient()**. This property represents the allowable hosts for the embed to run on. See the [Target Hostnames](https://support.airkit.com/docs/airclient-configurable-properties#target-hostnames) option above. The Host object has the following format:

```javascript JavaScript
interface AirClientHosts {  
  protocol: string  
  hostname: string  
}
```



## Sending Start Parameters

Start Parameters can be passed to an Airkit Embed like the following:

```javascript JavaScript
Airkit.createClient(deployId, frame).then((client) => {
    client.start(startParams)
})
```



Start parameters gets sent over the URL so there are limitations to the length (4K bytes), and will result in a 500 error if there is too much data being passed. If data needs to be passed to an application, using an App API would allow to pass more data. For more information on App APIs, see [Creating an API for your Airkit App](doc:creating-an-api-for-your-airkit-app).

## Instantiating airClient / JavaScript Functions

The following JavaScript functions can be run once the **airClient** has been instantiated.  The **airClient** can be instantiated by one of the following ways:

```javascript JavaScript
const airClient = window.Airkit.createClient(...)   
const session = airClient.start()   
// or   
const session = airClient.joinBySessionKey(sessionKey)   
// or   
const session = airClient.join(sessionId)
```



### JavaScript functions

**Returns the current session**

```javascript JavaScript
airClient.getSession()
```



**Triggers the help text popover to display**

```javascript JavaScript
airClient.showHint()
```



**Hides the help text popover**

```javascript JavaScript
airClient.hideHint() 
```



**Shows the launch button on the host page**

```javascript JavaScript
airClient.showLauncher() 
```



**Hides the launch button on the host page**

```javascript JavaScript
airClient.hideLauncher() 
```



**Shows the embedded application - this is the function that runs when the launch button is pressed**

```javascript JavaScript
airClient.show() 
```



**Hides the embedded application**

```javascript JavaScript
airClient.hide() 
```



**Removes (destroys) the embed including launch button from the page.  This is different from the .hide() function.**

```javascript JavaScript
airClient.remove() 
```



**Saves the current session ID in a cookie so that it can be reloaded.  This needs to be run for the .reload() function to run successfully.**

```javascript JavaScript
airClient.save() 
```



**Rejoins an existing session that was previously saved based on the browser's cookies**

```javascript JavaScript
airClient.reload() 
```



## Common Issues and Further Reading

For more information on what embeds are, check out [How to Embed an Airkit Experience on your Website](https://support.airkit.com/docs/embedding-an-airkit-experience-on-your-website).

For issues relating to CORS, or Cross-Origin Resource Sharing, ensure that the embed is being served from valid [Target Hostnames](#h_01F3N9ZZ7MSZ3HR7WCZNW5WZ80). If it is not, you will end up with an error.

Embeds require a published application, refer to [Publishing Your Application](https://support.airkit.com/docs/publishing-your-application) for information on how to publish apps so they are capable of being embedded.