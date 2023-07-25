Each Journey has a records standard pieces of data that are accessible to builders. This device data includes timezone, browser dimensions, timezone, and more. Please refer to the table below.


 


# Standard Journey Data


 




| Variable | Description | Scope Availability  |  Additional Notes |
|----|----|----|----|
| browser.width | Device width | Web Only | These variables can be used with some airscript to dynamically  |
browser.height | Device height | Web Only | These variables can be used with some airscript to dynamically  |
| session.timeZone | Timezone of the users device | Web Only | This is useful to enable [TCPA](https://support.airkit.com/docs/tcpa) |
| session.locale | Locale of the users device | Web Only | This provides you a sense of the users language. This can be helpful if you are building a localized experience. |
| channels.web.canvasLink | The unique URL to the customer’s journey.  | Global | You can include this in SMS to transfer your customer from SMS over to the Web Channel. |
| channels.voice.identifier | Phone Number of the user | Global (After Actor Configuration) |  |
| channels.message.identifier | Phone Number of the user | Global (After Actor Configuration) |  |
| session.id | The unique Journey Identifier that Airkit assigns | Global | This identifier (or a customer identifier) is necessary when creating App APIs |


 


# Additional Configuration Variables


 


In addition to the Standard Journey data, Theme variants and configuration properties are also available. Any of your theme variables can be accessed using the **theme** namespace. Configuration variables are available on the **configuration** namespace. Finally, custom profile variables and app specific configurations are available on **profile**. We recommend exploring these in App Preview to further see what data you have available.