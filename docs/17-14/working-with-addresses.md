There are multiple channels to collect an address from a user, from using a simple form or even through SMS. The addresses can be captured and written back into AirData or other external systems after they are collected. This article will walk through different ways to capture addresses, using the Place Search Input Control, text input controls, and through SMS. 


Capturing Addresses in a Form
-----------------------------

Forms provide a way to manually input an address during a journey. A simple form can be used as a manual entry process where the application has input fields for Address, City, State, and Zip Code. The place search input control can also be used within an application to auto-populate address fields or pass a formatted address to provide a more automated experience. This section will walk through how to create a simple form to capture addresses as well as show how to use the place search input control within a form as well. 


### Capturing addresses with a simple form

A simple form is a common way to capture a user's information. If looking to dive deeper on creating simple forms, see [Creating a Simple Form](https://support.airkit.com/docs/building-a-simple-form). The video below will walk through how to create a form that captures a user's address and submits it to AirData. 

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FD9zb043tXY0%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DD9zb043tXY0&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FD9zb043tXY0%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=D9zb043tXY0",
  "title": "Capturing an Address With a Simple Form",
  "favicon": "https://www.youtube.com/s/desktop/15c06292/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/D9zb043tXY0/hqdefault.jpg"
}
[/block]
**Prerequisites:**


* [App object](https://support.airkit.com/docs/airdata-app-objects) created in AirData named UserAddress with the following properties:
	- Text: `address_line_1`
	- Text: `address_line_2`
	- Text: `city`
	- Text: `state`
	- Text: `zip`


<img src="./assets_v1714/working-with-addresses-v1714-0.png" alt="organizing info" style="max-width: 350px; width:100%;"/>


### Capturing address with the Place Search Input Control


The Place Search Input control can be used to capture an address and can even be used to auto-populate form fields to allow for further editing. This example will walk through how to get a formatted address from the place search input control as well as use other outputs to add to form fields. 


**Pre-Requisites:**


* Have a simple form built to capture address as shown in [Capturing addresses with a simple form](#h_01F2SW57T1RCJVBDV2XMCH1MWC).


First, build out a Place app object and an addressComponents app object to use as variable types. Add a **Place Object** in AirData and name it 'Place'.


<img src="./assets_v1714/working-with-addresses-v1714-1.png" alt="organizing info" style="max-width: 200px; width:100%;"/>

Add an app object in AirData and name it 'addressComponents'. Add the following fields as text fields: address, city, state, zip, country. The app object should look like this:




[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/working-with-addresses-v1714-2.png",
        "mceclip0 (1)-address.png",
        319,
        219,
        "#fbfbfb"
      ]
    }
  ]
}
[/block]
Then add the addressComponent field in the Place app object and rename the field to `addressComponents`.


<img src="./assets_v1714/working-with-addresses-v1714-3.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

The Place app object should look like this:


<img src="./assets_v1714/working-with-addresses-v1714-4.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

**Note**: Building out the app object for the search results and location is an optional step, as the example will still work by simply using the variable type **Any** for the variables created. By building out the app object manually, this facilitates the use of the typeahead functionality.


Add a **Place Search Input** control to the Web Page. 

<img src="./assets_v1714/working-with-addresses-v1714-5.png" alt="organizing info" style="max-width: 450px; width:100%;"/>



Change the **searchType** property on the control to from nearby to **autocomplete**. 

<img src="./assets_v1714/working-with-addresses-v1714-6.png" alt="organizing info" style="max-width: 250px; width:100%;"/>



On the Web Page, add two variables of the type **Any** and name one `location` and the other `search_results`. This is where the search results are going to be stored from the place search input control. 


<img src="./assets_v1714/working-with-addresses-v1714-7.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Select the Place Search Input control and go to the actions tab in the inspector. Under the **Search Results Changed** event, add a [Set Variable](https://support.airkit.com/reference/the-set-variable-action) action and set `search_results` to `event.value`. Add an additional Set Variable action and set `location` to `search_results[0]`. 

<img src="./assets_v1714/working-with-addresses-v1714-8.png" alt="organizing info" style="max-width: 500px; width:100%;"/>

With the `location` variable set to `search_results[0]`, whenever a user searches and selects an address, the results can be surfaced through the location variable. For more information on how to capture addresses in a variable, see [Working with the Users Current Location](https://support.airkit.com/docs/working-with-the-users-current-location). The place search input control provides both a formatted address as well as a parsed address that can be retrieved by `addressComponents`. The output looks like the below:



```json Airscript
[  
  {  
    "latitude": 37.4285713,  
    "longitude": -122.1434025,  
    "formattedAddress": "200 California Ave, Palo Alto, CA 94306, USA",  
    "addressComponents": {  
      "address": "200 California Ave",  
      "city": "Palo Alto",  
      "state": "CA",  
      "zip": "94306",  
      "country": "US"  
    },  
  "identifier": "<identifier>",  
  "name": "200 California Ave",  
  "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/v1/png_71/geocode-71.png"  
  }  
] 
```

 Next, change the values property on each of the address input controls to the proper addressComponent property. For example, for Address Line 1, change the value to `location.addressComponents.address`.


![mceclip6.png](./assets_v1714/working-with-addresses-v1714-9.png)


Continue the process with the City input, State input, and Zip Code input:


* City: `location.addressComponents.city`
* State: `location.addressComponents.state`
* Zip Code: `location.addressComponents.zip`


Save the application and go to **App Preview**. The address lines should get auto populated after typing in an address in the place search!


 
<img src="./assets_v1714/working-with-addresses-v1714-10.gif" alt="organizing info" style="max-width: 350px; width:100%;"/>




Capturing addresses in a Chat Bot
---------------------------------


Another method to capture addresses is through a chat bot. Although it is recommended to send a user a link to direct them to a web experience when capturing addresses, using a chat bot to capture information is possible as well. This example will walk through capturing individual fields of an address and storing them in a variable using a chat bot.


In Web Builder, go to Chat Bots in the tree and select 'My First Chat Bot'. In the inspector, add the following variables:


* Text: **address**
* Text: **city**
* Text: **state**
* Text: **zip**


<img src="./assets_v1714/working-with-addresses-v1714-11.png" alt="organizing info" style="max-width: 250px; width:100%;"/>

Then remove 'My First Chat Prompt' and add four Text Response Capture controls, one for each address field. Rename the Text Response captures accordingly. 


<img src="./assets_v1714/working-with-addresses-v1714-12.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

Select 'My First Chat Bot' and in the inspector, select 'Address Text Response Capture' as the Initial Chat Prompt.


<img src="./assets_v1714/working-with-addresses-v1714-13.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

Next, select 'Address Text Response Capture' and change the message text to "Please enter your address:" or any other text that is preferable. Then go to the inspector and under the Text Response Capture event, enter `address` to the Variable Binding. 


<img src="./assets_v1714/working-with-addresses-v1714-14.png" alt="organizing info" style="max-width: 600px; width:100%;"/>

Then in the next message, select the City Text Response Capture to go to the next response and capture the city from the user.   

<img src="./assets_v1714/working-with-addresses-v1714-15.png" alt="organizing info" style="max-width: 500px; width:100%;"/>

Repeat these steps for the City response capture, State response capture, and Zip response capture. For each particular field, bind the corresponding variable to the text response capture. So for the city response capture, bind the variable to **city**. For the state response capture, bind the variable to **state**. And lastly for the zip response capture, bind the variable to **zip**.  Once all of the text response captures are configured, save the application and go to **App Preview**. Click on the chat icon at the bottom of the preview to open up a chat preview experience.


<img src="./assets_v1714/working-with-addresses-v1714-16.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

To invoke the chat bot, type in a message like 'hello'. There is also the option to add a [Start Chat Bot action](https://support.airkit.com/reference/the-start-chat-bot-action) on the Journey start so that is invoked when the journey starts. After sending the first message, the chat bot should respond by asking "Please enter your address:". After entering in an address, the chat bot will go through the actions and then ask the city, state, and zip. Each address field is then stored in their respective variable and can be used throughout the journey, like storing it in AirData or passing it to another system. 

<img src="./assets_v1714/working-with-addresses-v1714-17.png" alt="organizing info" style="max-width: 450px; width:100%;"/>