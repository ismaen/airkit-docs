When a [Journey](doc:journeys)  begins with an incoming call or text message, relevant starting parameters – such as the phone number and location of the caller – are automatically saved in the session namespace. This document discusses the significance of this information as a [Journey identifier](doc:journeys), exactly what information is saved, and how it can be accessed throughout the course of a Journey.


### Context and Overview

As an [Actor](doc:actors) goes through a Journey, it is often necessary to temporarily store information regarding details pertinent to that Journey. These variables are not saved permanently to AirData and are lost when a Journey ends, but they are accessible at different or all points throughout a user Journey, depending on their [variables scopes](doc:variable-scopes). Variables stored at the session-level can be accessed at any point throughout an active Journey.

Among the most common variables stored at the session-level are start parameters: information defined as soon as a Journey begins. This information includes a unique Journey identifier, which can be used to recognize existing Journeys should a user wish to access the application through other channels. How this Identifier is defined depends on what information is available at the start of a Journey, which is itself dependent on how that Journey was initially triggered. A Journey that begins when a user sends a text message, for instance, will immediately and automatically have access to the the unique phone number of the Actor, while a Journey that begins when a user clicks on a web link will not.

When Journey is triggered by an incoming call or text message, fundamental information regarding the phone of the Action is automatically saved to the session namespace. Like all other variables saved at the session level, this information can be called on throughout the Journey. Common use cases for it include:

*   Recognizing the Actor should they call or text again while their Journey is still active.
*   Sending follow-up calls or texts to the stored phone number.
*   Utilizing the country the call was sent from in order to properly format dates, numbers, or currency.

### Format of Captured Information

As a rule of thumb, starting parameters are saved in the automatically-generated object **session**. When a Journey begins with an incoming call or text message, the object **session** is formatted as follows. Note that this example contains, in many instances, the filler "XXX" instead of any identifying information; this example is meant to showcase the structure of the object rather than communicate information about a particular call:


[block:code]
{
  "codes": [
    {
      "code": "{  \n\"id\": \"XXX\",  \n\"start\": {  \n  \"call\": {  \n    \"To\": \"+XXX\",  \n    \"From\": \"+XXX\",  \n    \"ToZip\": null,  \n    \"Called\": \"+XXX\",   \n    \"Caller\": \"+XXX\",  \n    \"ToCity\": null,  \n    \"CallSid\": \"XXX\",  \n    \"FromZip\": \"XXX\",  \n    \"ToState\": null,  \n    \"FromCity\": \"XXX\",  \n    \"CalledZip\": null,  \n    \"CallerZip\": \"XXX\",  \n    \"Direction\": \"inbound\",  \n    \"FromState\": \"CA\",  \n    \"ToCountry\": \"US\",  \n    \"AccountSid\": \"XXX\",  \n    \"ApiVersion\": \"2010-04-01\",  \n    \"CallStatus\": \"ringing\",  \n    \"CalledCity\": null,  \n    \"CallerCity\": \"XXX\",  \n    \"CalledState\": null,  \n    \"CallerState\": \"CA\",  \n    \"FromCountry\": \"US\",  \n    \"CalledCountry\": \"US\",  \n    \"CallerCountry\": \"US\"   \n   },  \n  \"phone\": \"+XXX\"  \n },  \n\"timeZone\": \"America/Los_Angeles\",  \n\"locale\": \"en-us\"  \n}",
      "language": "json"
    }
  ]
}
[/block]
### Capturing and Accessing Caller Information

When a Journey begins with an incoming call or SMS, information pertaining to the call will be automatically stored under **session.start.call**, which can be accessed throughout a Journey the same way as any other locally stored variable. For instance, calling on the variable **session.start.call** will provide you with access to all information captured from from the incoming call or text that triggered the start of the Journey. Both **session.start.phone** and **session.start.call.caller** will specify the phone number that the incoming call or text came from.

#### Starting a Journey with an incoming call or SMS

In order to deploy an app that begins with an incoming call or SMS message, you must build you app as follows:

1.  Declare Calls a Number, Sends a Message, or both as the Starting Event within the Journey Builder.  
    *   This can be done in the [Starting Events](doc:starting-events) branch of the Tree, or as one of the first thing you do upon creating an app.
2.  Connect the starting event to a Voice Bot or Chat Bot. 
3.  [Configure a number to take incoming calls](doc:connecting-your-twilio-numbers-to-airkit) .