Many apps require communication with users via email. For example, sending email confirmation for a scheduled phone call or order confirmation. 

Setting up a Verified Address to Send Email **From**
----------------------------------------------------


A *From* address is required to send emails. Airkit allows for the configuration of different addresses to send emails from. To configure an email, go to [Console](https://support.airkit.com/docs/console). Under the Resources section, select *New*.


There are two options that deal with email. Select *Email Address* and type in a valid email address. Click create. This will allow this email address to be used to send emails. Once create is clicked, Airkit will trigger an authorization email from AWS. Check the email address and click the link to verify the email address. This will enable this email address for sending. Refresh the console page and select the email address. Notice that the *Verification Status* is set to "Success."


### Example AWS Verification Email with Link to Verify


![2021-04-16_08-33-26.png](./assets_v1714/sending-email-from-airkit-v1714-0.png)


Setting up Your Domain to Ensure Smooth Delivery (DMARC)
--------------------------------------------------------


It is **ALWAYS** a good idea to setup a domain level verification to ensure smooth delivery so that emails are not caught in anti-spam filtering tools.  In order to do this, a few DNS records will be needed to be added to the domain used in the email address that is in the desired from email address.  Although the act of adding these records typically only takes a few minutes, it is a privileged request in many organizations and may require some lead time (please verify domains early).


To verify a domain, in [Console:](https://support.airkit.com/docs/console) 


1. Console > Resources > select ***New***
2. Under *Capabilities,* select the "Email Domain".
3. Enter the domain in the provided box > Click create
4. Select the new domain from the list. Click the "Open verification instructions" button


### Example DNS Setup Instructions for Verifying Domain


![2021-04-16_08-55-02.png](./assets_v1714/sending-email-from-airkit-v1714-1.png)


In order to set up verification of the domain, a TXT record will be required. To enable DKIM for email verification, additional CNAME records will be required. Once the DNS has been updated, the domain verification will be automatically verified within Airkit, although this process might work within minutes, it could take up to 72 hours depending on DNS settings.


 


Adding Verified Email Addresses to an App
-----------------------------------------


Go to your App, go to [Configuration Builder](https://support.airkit.com/docs/configuration-builder), and scroll down to the *Emails* section. Select the *New* button.


![Airhome-SendEmail-AddEmail.png](./assets_v1714/sending-email-from-airkit-v1714-2.png)


Options will be available based on settings configured in the *Console* above. Adding a singular email address will present a dropdown of configured, available email addresses. Choosing *Email Domain Address* will present a box for an address and a dropdown for qualified domains. Make sure that at least one email is created, as it will be required to send an email.


Using the Send Email Data Operation
-----------------------------------


 Go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and create a new data flow, label it "Email - Send Thanks." In the *From* dropdown, select the email address. Type a valid email in the *To* field. In order to verify that the send works, this email address will have to be checked. In the *Subject,* field add the text "Thank you for your interest in our properties." For the text body:



```
"Here at AirHome, we go out of our way to provide you with the best experience   
possible. Thanks for showing interest in our properties. If you have any further  
questions, please don't hesitate to reach out."
```


Hit the play button at the top right of the data operation. The response in the run results should return "true." Checking addressed email should result in a new message with the specified content.


Testing Sending Email
---------------------


Once a verified email address & domain have been setup we recommend using an external email testing tool such as <https://www.mail-tester.com> to confirm the ability to send/receive email on behalf of the verified email/domain and also get a report on the DMARC (anti-spam) configurations of the account.  Setting up DMARC properly will ensure more delivered emails.  
![mceclip0.png](./assets_v1714/sending-email-from-airkit-v1714-3.png)


 


Customizing Email
-----------------


Beyond sending generic emails, it is possible to customize the addresses, subject, body and even provide an HTML body of an email.


Add an input to the "Email - Send Thanks" Data Flow of type List of Text and name it **emails**. Add a second input of List of Houses (if there is no House Object, do list of Any) and name it **houses**. Set the emails to a list of valid emails of the format:



```javascript Airscript
["foo@bar.com", "bar@example.com"]
```

Set the houses to object to an array of houses:



```json Airscript
[{  
  "image": {  
    "id": "946c295f-684f-41be-a2ed-2f90df70c35d",  
    "assetKey": "ab69d4c4-5ff9-42b5-b8c7-7e479cc0bbba",  
    "organizationId": "395f62e5-6437-4ef0-9505-8a21a4c89e0b",  
    "visibility": "GLOBAL",  
    "version": 0  
  },  
  "baths": 2,  
  "asking": {  
    "amount": 30000000,  
    "precision": 2,  
    "code": "USD"  
  },  
  "square_feet": 3252,  
  "beds": 3,  
  "date_available": {  
    "year": 2021,  
    "month": 4,  
    "day": 7  
  },  
  "title": "Little Prairie",  
  "contact_email": "bob@example.com"  
},  
{  
  "__id": "4ab32f3a-b0ea-4c6d-b8e9-741dfd559a64",  
  "image": {  
    "id": "a2416138-d560-4ef4-ab40-f2a38549ddbc",  
    "assetKey": "ab69d4c4-5ff9-42b5-b8c7-7e479cc0bbba",  
    "organizationId": "395f62e5-6437-4ef0-9505-8a21a4c89e0b",  
    "visibility": "GLOBAL",  
    "version": 0  
  },  
  "baths": 1.5,  
  "asking": {  
    "amount": 40000000,  
    "precision": 2,  
    "code": "USD"  
  },  
  "square_feet": 2356,  
  "beds": 4,  
  "date_available": {  
    "year": 2021,  
    "month": 11,  
    "day": 8  
  },  
  "title": "Ranch 12",  
  "contact_email": "roger@example.com"  
}]
```

The *To* field on *Send Email* action will work with either a text value of comma-separated email addresses or a list of email address text strings. Put the value **emails** in the *To*field of the Send Email action.


The houses are an AirData App Object. Let's configure our message to contain information about the houses sent in. Create another Data Operation above the email. Select type Transform from the dropdown. Enter the following Airscript into the *Transform Expression:*



```javascript Airscript
JOIN(  
  FROM h IN houses SELECT "{{h.title}}, {{FORMAT_CURRENCY(h.asking)}}",  
  "\n"  
)
```

This will take the title and asking price from each house output them in a text string. For more information, check out [Working with Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript). Update the body text of the *Send Email* action to:



```
"Here at AirHome, we go out of our way to provide you with the best experience  
possible. Thanks for showing interest in our properties. Our records show you are  
interested in these properties:  
   
{{transform}}  
  
If you have any further questions, please don't hesitate to reach out."
```

Hitting play on this action will now send an email with properties listed.


HTML Styling
------------


In addition to sending plain text email, it is also possible to send HTML email. It is possible to send  an email with both a plain text and HTML version. Your email client will render the option that is most appropriate for rendering. Set the Body HTML of the send email action to:



```html
"<h1>Thanks!</h1>  
  
<p>Here at <em>AirHome</em>, we go out of our way to provide you with the best experience  
possible. Thanks for showing interest in our properties. Our records show you are  
interested in these properties:</p>  
  
<div style=\"font-size:1.5em;\">  
{{  
SUBSTITUTE(  
transform,  
"\n",  
"<br />"  
)  
}}  
</div>  
  
<p>If you have any further questions, please don't hesitate to reach out.</p>"
```

Sending the email now should return a stylized email.


![Airhome-SendEmail-HTMLemail.png](./assets_v1714/sending-email-from-airkit-v1714-4.png)


This is just one example of how to use email in Airkit. Other examples include sending event registration, sending completed documents, or other confirmation emails.


Further Reading
---------------


* [The Send Email Data Operation](https://support.airkit.com/reference/the-send-email-data-operation) - for more of the details on how the Send Email Data Operation works.
* [Working with Files & Media](https://support.airkit.com/docs/working-with-files-and-media) - for information on assets that can be sent as email attachments.