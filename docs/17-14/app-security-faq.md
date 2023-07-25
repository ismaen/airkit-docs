Overview
--------


Here is a compiled list of common questions and answers around building secure apps with Airkit, ranging from best practices around TCPA, Airdata security and retention, session expiry, and more. 


General
-------


#### Are data flows run server-side or client-side?


Data flows are run server-side, which is why they have inputs and outputs. Data that is stored at the session namespace, activity group namespace, or activity namespace is stored on the client and accessible through the browser. For more information on variables scopes, see [here](https://support.airkit.com/docs/variable-scopes). 
#### How long do sessions last?


By default, sessions have an expiration of 30 days. Session expiration time can be configured in [Configuration Builder.](https://support.airkit.com/docs/configuration-builder) Journey's can also be extended using the [Extend Journey Expiration Time](https://support.airkit.com/reference/the-extend-journey-expiration-time-action) action in an action chain as well. 


#### How do you know if a session/journey has been completed?


Session Activity can be monitored and seen by clicking on the menu icon > **Sessions and Activity** when editing an application in the studio. Journey's can also be ended manually by using the [End Journey](https://support.airkit.com/reference/the-end-journey-action) action in an action chain. 


#### Can I build an app that requires authentication?


Yes, in Airkit there is the concept of Public Apps, Secure Apps and Authentication Apps, which can be configured in [Configuration Builder](https://support.airkit.com/docs/configuration-builder). Public apps can be accessed from anyone and are open to the public for access. Secure apps can only be accessed by being redirected through an Authentication app. The Authentication App is typically a generic app that asks for a username/password (password is a secure text input control), and when submitted, calls the [set authentication action](https://support.airkit.com/reference/the-set-authentication-action). If the username/password matches the authentication parameters, then the set authentication action redirects the user to the secure app journey. The secure app also has a cookie that can be set, which will redirect the user back to the authentication app when it is expired. 
#### Are assets uploaded to the [Media Library](https://support.airkit.com/docs/media-library) scanned for any malware or viruses?


Yes, assets uploaded to the Media library are scanned for trojans, malware, viruses and other threats. If a malicious file is detected, the asset will be rejected.   

#### Are my API tokens in console secure?


Yes, API tokens and credentials that are uploaded via integrations are stored in an encrypted vault.



Data
----


#### Where is data in Airdata stored, and is it secure?


Airdata is encrypted at rest, encrypted in transit between systems and encrypted on the server itself.  Our online infrastructure is built on Amazon Web Services, which maintains an extensive set of certifications including SOC2, ISO 27001, and FEDRAMP that cover the service’s security, confidentiality, availability, and integrity. For more information, see <https://www.airkit.com/security/>.


#### How long is data retained?


Data stored in Airdata is retained unless it is manually deleted. Session data, on the other hand, is stored for the length of the session duration. Session duration is configurable by the user in configuration builder and can also be extended by using the [The Extend Journey Expiration Time Action](https://support.airkit.com/reference/the-extend-journey-expiration-time-action). 


#### Where is the data from inputs or variables stored?


Data that is input on the client is saved on the browser. If using the [secure text input control](https://support.airkit.com/reference/secure-text-input-web-control), the values input into that control are not surfaced on the browser. Using the secure text input control generates a redis key that can be accessed through a data flow using the [The Secure Value Retrieval Data Operation](https://support.airkit.com/reference/the-secure-value-retrieval-data-operation).


#### How are assets retained on Airkit servers?


Assets in Airkit are uploaded to Amazon S3, in a separate bucket per org, per application. Assets can either created as a global asset or a private asset. Global assets are available on the CDN with a static link. Private assets have a generated link and has an expiration time which is configurable. See [The Asset Data Type](https://support.airkit.com/reference/the-asset-data-type) for more information.


#### How do I handle secure data when building in Airkit?


Secure data can be handled by using the [Secure Text Input Web Control](https://support.airkit.com/reference/secure-text-input-web-control), [Secure Touchtone Capture Control](https://support.airkit.com/reference/secure-touchtone-capture-control), or by using PCI compliant controls such as the [Credit Card Control](https://support.airkit.com/reference/credit-card-web-control) or the [Payment Request Button Control](https://support.airkit.com/reference/payment-request-button-web-control). 


#### How are emails handled in Airkit?


When using the [The Send Email Data Operation](https://support.airkit.com/reference/the-send-email-data-operation), emails get routed through Amazon SES and do not sit on Airkit servers.
TCPA
----


#### What are some best practices for building an application that is TCPA compliant?


The best way to ensure TCPA compliance when building out an application, is to first be able to extract a user's state and timezone locale. The best way to do this, is to ask for a user's zipcode, and use a zipcode lookup API to extract state and timezone. Using this information, chat/voice bots can be triggered on [timers](https://support.airkit.com/docs/journey-specific-timers-and-reminders) that can be restricted to only run based on a TCPA calendar. The calendar restriction must be to either **Do not schedule and cancel** or **Schedule in next available time slot**. For more information on TCPA, see [How To enforce TCPA](https://support.airkit.com/docs/how-to-enforce-tcpa).
PCI Compliance
--------------


#### What are best practices when building a PCI compliant application?


When building a PCI compliant app, ensure that no sensitive data is saved on the client. Data that is deemed sensitive should use the [Secure Text Input Web Control](https://support.airkit.com/reference/secure-text-input-web-control), and pass that data to be retrieved server side, through a data flow. Also, data that is passed to the data flow should not be returned as an output, or else the application is no longer PCI compliant. Also, when capturing credit card information, Airkit has PCI specific controls that are PCI compliant out of the box, such as [Credit Card Web Control](https://support.airkit.com/reference/credit-card-web-control) and the [Payment Request Button Web Control](https://support.airkit.com/reference/payment-request-button-web-control).