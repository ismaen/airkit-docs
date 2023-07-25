This document goes over how to enforce [TCPA](https://support.airkit.com/docs/tcpa) within the Airkit Platform.


Introduction
------------


TCPA (Telephone Consumer Protection Act) is a series of US legislation that dictates how automated systems can reach out to customers over SMS and Voice. These limitations typically involve:


* Restrictions on time of day messages can be sent
* Restrictions on holidays
* Allowing the User to Opt-Out


The Airkit platform provides TCPA calendars available per state and timezone. Airkit creates these calendars to help facilitate the implementation of TCPA for your specific application.


### When to be concerned about TCPA


TCPA is important for all external communication with a consumer that occurs over SMS and/or Voice. If application is an internal only application, or does not contact people on those channels, then you don’t need to worry about TCPA. However, it’s highly recommended to enable this for any external communication with a customer.


Further considerations should be made when involving non-SMS and non-Voice channels of communication. For example, the TCPA regulation still applies if you are sending internet-to-phone messages such as WhatsApp, Hangouts, and other voice over IP / chat over data operations.


Finally, you can provide additional assurances by explicity getting an opt-in from the consumer. Typically, this is accomplished by having a phone number that the user themselves enter (either on Airkit or on your own system). This opt-in ensures that the consumer has initially consented to messages, and provides you permission to do so with less restrictions. While opting-in is highly encouraged, it is not absolutely necessary to stay compliant.


### Steps to enable TCPA timing restrictions


#### 1. Identify State and Timezone of the user


We need establish the users current state and [timezone locale](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (eg. America/Los_Angeles). One way to accomplish this is by utilizing a [3rd Party API](https://rapidapi.com/redline/api/redline-zipcode) to look this information up based on zipcode. Once you establish the users State & Timezone, save these to a variable so they can be used in later steps.


#### 2. Add Calendar Restrictions to Relevant Timers


On any timer, you can control whether the timer should be adjusted via a calendar. This mechanism allows us to apply TCPA restrictions on these timers. For TCPA, you’ll select the custom expression option. Your custom expression should match the format: **TCPA-{{state_variable}}-{{timezone_variable}}** . After entering that expression, you can decide what to do if the time is not available. To stay TCPA compliant, you **must** select either **Do not schedule and cancel** or **Schedule in next available time slot**.


#### 3. Test your restrictions


It's important to test your new timer restrictions in [Preview Mode](https://support.airkit.com/docs/app-preview). Make sure that the behavior you expect (either canceling the event or scheduling it for the next available time) is correct for your application.


### Steps to add TCPA opt-out (For Chat Prompts)


It’s important to note that the following keyword matchers must be on every chat prompt configured. Additionally, you must include language in your first out-going SMS that references the availability of the STOP command (eg. STOP2STOP, STOP=end, etc.)


*Twilio (Airkit’s main voice provider) enables TCPA support by default. These steps assume that default TCPA logic is in place. If it is not, please reach out to [support@airkit.com](mailto:support@airkit.com) for additional information*.


#### 1. Create an opt-out keyword matcher


Navigate to the conversation builder and add a decision option. Once you’ve added a decision option, add the following keyword matchers:


* STOP
* STOPALL
* UNSUBSCRIBE
* CANCEL
* END
* QUIT


After setting up the decision option, create an additional chat prompt. This chat prompt will be the response message: the opt-out message. Once you’ve configured that message, go back to the original chat prompt’s decision option and select the newly created chat prompt on the decision option you previously configured.


#### 2. Create a help keyword matcher


Navigate to the conversation builder and add a decision option. Once you’ve added a decision option, add the following keyword matchers:


* HELP
* INFO


After setting up the decision option, create an additional chat prompt. This chat prompt will be the response message - the opt-out message. Once you’ve configured that message, go back to the original chat prompt’s decision option and select the newly created chat prompt on the decision option you previously configured.


### Steps to add TCPA opt-out (For Voice Prompts)


For Voice calls, it’s important that the message establishes the intent of the phone call in the first 15 seconds. When configuring your message, make sure to be clear who the phone call is representing and the purpose of the call.


#### 1. Create an opt-out DTMF


On Voice prompts, you must add a DTMF matcher to each one. To do so, navigate to the conversation builder and add a decision option. Once you’ve added a decision option, add the following keyword matchers:


* STOP
* STOPALL
* UNSUBSCRIBE
* CANCEL
* END
* QUIT


Since this is voice, you should also alter the message presented to the user to include the opt-out option.


After setting up the decision option, create an additional voice prompt. This voice prompt will be the response message - the opt-out message. Once you’ve configured that message, go back to the original voice prompt’s decision option and select the newly created voice prompt on the decision option you previously configured.