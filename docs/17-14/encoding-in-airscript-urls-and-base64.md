When working with external systems nearly all communications will be done through data of [The Text Variable Data Type](https://support.airkit.com/reference/the-text-variable-data-type). For example, when sending an App Object thrugh an [HTTP Request Data Operation](https://support.airkit.com/reference/http-request-data-operation) the app Object will typically be encoded as JSON. Airkit provides functions to help encode data as Text for different common use cases.

## JSON Encoding

JSON is a very common for encoding complex data such as [Lists](https://support.airkit.com/reference/the-list-data-type) or App Objects to Text. The [TO_JSON](https://support.airkit.com/reference/to_json), and [FROM_JSON](https://support.airkit.com/reference/from_json) functions can encode/decode all types to and from JSON. For example, if we were to encode this library listing to JSON:

```javascript Airscript
TO_JSON([  
  {  
    name: "John Doe",  
    number: 5  
  },  
  {  
    name: "Jane Doe",  
    number: 6  
  }  
])
```



the result would be the following JSON

```json JSON
[  
  {  
    "name": "John Doe",  
    "number": 5  
  },  
  {  
    "name": "Jane Doe",  
    "number": 6  
  }  
]
```



Also note, that JSON is valid Airscript. This makes it very convenient to copy paste JSON into an Expression Editor.

Values of the [Datetime](https://support.airkit.com/reference/the-datetime-variable-data-type), [Date](https://support.airkit.com/reference/the-date-variable-data-type), and [Time](https://support.airkit.com/reference/the-time-variable-data-type) types encode to JSON as objects, however, external systems will often have unique encodings for these types. See [Working with Date, Time & DateTime in Airscript](https://support.airkit.com/docs/working-with-date,-time-and-datetime-in-airscript) for information about common encodings of Dates and Datetimes.

Values of the [Currency](https://support.airkit.com/reference/the-currency-variable-data-type) type are likely to have different encodings with different external systems. See [Working with Numbers and Currency in Airscript](https://support.airkit.com/docs/working-with-numbers-and-currency-in-airscript) for information on how to encode a Currency in Text.

## URL Encoding

When developing a web application it is often useful to embed data in the url of a web page. Search engines will often encode the query in a URL Query Parameter, for example a Google search for airkit has **q=airkit** at the end of the url: <https://www.google.com/search?q=airkit>. However, notice that search for the term **low code** needs special treatment because of the space: <https://www.google.com/search?q=low%20code>. Use the [URL_ENCODE](https://support.airkit.com/reference/url_encode) and [URL_DECODE](https://support.airkit.com/reference/url_decode) functions to encode and decode text for use in URLs.

```javascript Airscript
"https://www.google.com/search?q={{URL_ENCODE(example_search_query)}}"
```



Note, however, that when using an [HTTP Request Data Operation](https://support.airkit.com/reference/http-request-data-operation) query parameters can be entered separately from the URL, in such a case the parameters will be automatically encoded so the  [URL_ENCODE](https://support.airkit.com/reference/url_encode) function should not be used.

## Base64 Encoding

While JSON is a way to encode more complex data types such as [Lists](https://support.airkit.com/reference/the-list-data-type) and Objects into [Text](https://support.airkit.com/reference/the-text-variable-data-type), more complex data such as images or video are commonly encoded using Base64. While Airscript cannot directly access the internal data of images or videos, there are scenarios where [Text](https://support.airkit.com/reference/the-text-variable-data-type) may need to be encoded or decoded when working with an external system. The [BASE64_ENCODE](https://support.airkit.com/reference/base64_encode) and [BASE64_DECODE](https://support.airkit.com/reference/base64_decode) functions can be used in these cases.

## Relevant Functions

- [TO_JSON](https://support.airkit.com/reference/to_json)
- [FROM_JSON](https://support.airkit.com/reference/from_json)
- [URL_ENCODE](https://support.airkit.com/reference/url_encode)
- [URL_DECODE](https://support.airkit.com/reference/url_decode)
- [BASE64_ENCODE](https://support.airkit.com/reference/base64_encode)
- [BASE64_DECODE](https://support.airkit.com/reference/base64_decode)
- [DATETIME_FROM_TIMESTAMP](https://support.airkit.com/reference/datetime_from_timestamp)
- [TIMESTAMP_FROM_DATETIME](https://support.airkit.com/reference/timestamp_from_datetime)
- [FORMAT_DATETIME](https://support.airkit.com/reference/format_datetime)
- [DATETIME_FROM_FORMAT](https://support.airkit.com/reference/datetime_from_format)
- [DATE_FROM_FORMAT](https://support.airkit.com/reference/date_from_format)
- [FORMAT_DATE](https://support.airkit.com/reference/format_date)
- [FORMAT_TIME](https://support.airkit.com/reference/format_time)
- [TIME_FROM_FORMAT](https://support.airkit.com/reference/time_from_format)