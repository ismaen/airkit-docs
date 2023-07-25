When capturing emails and phone numbers from users it is important to ensure the information is indeed valid so that it can be used to send outgoing messages. Attempting to send emails to non-existent email addresses, and calling or sending text messages to invalid phone numbers can adversely affect spam scores. The [ISEMAIL](https://support.airkit.com/reference/isemail) function will return **TRUE** when provided a string that appears to be a valid email address. The [ISPHONE](https://support.airkit.com/reference/isphone) function will return **TRUE** when provided a string that appears to be an E-164 formatted phone number.


While the properly formatted E-164 phone number stored on the Actor is needed to ensure when interacting with the user over Voice or SMS, users are used to seeing phone numbers formatted in different ways depending on their locale. The [FORMAT_PHONE](https://support.airkit.com/reference/format_phone) function will display an E-164 string in various formats.



```javascript Airscript
FORMAT_PHONE("+15558675309", "NATIONAL") => "(555) 867-5309"
```

Relevant Functions
------------------


* [ISEMAIL](https://support.airkit.com/reference/isemail)
* [ISPHONE](https://support.airkit.com/reference/isphone)
* [PARSE_PHONE](https://support.airkit.com/reference/parse_phone)
* [FORMAT_PHONE](https://support.airkit.com/reference/format_phone)