The [Text](https://support.airkit.com/reference/the-text-variable-data-type) type in Airscript is used to hold written text that might be displayed to the user in a [Label Web Control](https://support.airkit.com/reference/label-web-control). The text type is also used when capturing information from a user such as a name, an address, or phone number. In addition to using the Text type to store real-world information, the Text type is also often used to store data used by computers, such as a unique identifier or the status of an ongoing sales opportunity. Airkit provides a suite of useful utilities to help work with data of this nature.


*Note: In Airscript, as in many other programming languages., a particular instance of the text type is often referred to as a String.*


To create Text (a string), enclose the text with the double-quote character (**"**)



```javascript Airscript
"Hello world!"
```

For the majority of use cases, it is useful to think of a string as a sequence of characters such as **a**, **b,** or even special characters such as **-**, **%**, or really any other character that might be needed. The number of characters in a string can be obtained with the [LENGTH](https://support.airkit.com/reference/length) function. For example, the length of the string **"Hello world"** is **12**.



```javascript Airscript
LENGTH("Hello world!") => 12
```

*Note: The definition of a character may not always be what you expect, for example, the "Slightly Smiling Face" emoji (*🙂*) as well as many non-English characters are actually made up of two or more characters. See [The Text Variable Data Type](https://support.airkit.com/reference/the-text-variable-data-type) for more information.*


Convenience Utilities
---------------------


There are a number of routine operations needed for dealing with strings.


When accepting input from a user you may want to remove extra whitespace, for example, if the user enters an extra space at the end of their name you will likely want to remove it so that you store their name as **"John Smith"** rather than **"John Smith "**. The [TRIM](https://support.airkit.com/reference/trim) function removes spaces, tabs, newlines, and other whitespace from the beginning and end of a string.



```javascript Airscript
TRIM("  Hello world!   ") => "Hello world!"
```

There are times that you may want to repeat a given string a certain number of times, for example repeating the string **"abc"** three times to get the string **"abcabcabc"**. See the [REPT](https://support.airkit.com/reference/rept) and [PADSTRING](https://support.airkit.com/reference/padstring) functions for this.


It is also fairly routine to ensure a string contains only lowercase or uppercase characters. The [LOWERCASE](https://support.airkit.com/reference/lowercase) and [UPPERCASE](https://support.airkit.com/reference/uppercase) functions will do just that.



```javascript Airscript
LOWERCASE("Hello world!") => "hello world!"  
UPPERCASE("Hello world!") => "HELLO WORLD!"
```

Searching and Ordering
----------------------


A substring is a smaller string contained inside a larger string. Both **"Hello"**, and **"world"** are substrings of the string **"Hello world"**. The [SUBSTRING](https://support.airkit.com/reference/substring) function extracts substrings from a larger string using a starting and ending position inside the string.



```javascript Airscript
SUBSTRING("**Hello** world!", 0, 5) => "Hello"  
SUBSTRING("Hello **world**!", 6, 11) => "world"
```

Although you may not always know ahead of time the position of a substring. In these cases use the [STRING_FIND](https://support.airkit.com/reference/string_find) function to find the beginning of a substring. If the result is **-1** it means the substring was not found.



```javascript Airscript
STRING_FIND("Hello world!", "Hello") => 0  
STRING_FIND("Hello world!", "world") => 6  
STRING_FIND("Hello world!", "bananas") => -1
```

You may be interested in whether one string is alphabetically smaller than another. The [STRING_COMPARE](https://support.airkit.com/reference/string_compare) function will determine this by returning a negative number if the first string is smaller than the second, **0** if the strings are the same, and a positive number if the first string is larger than the second



```javascript Airscript
STRING_COMPARE("Hello", "world") => negative  
STRING_COMPARE("world", "Hello") => positive  
STRING_COMPARE("world", "world") => 0  
STRING_COMPARE("world", "World") => negative  
STRING_COMPARE("World", "world") => positive  
STRING_COMPARE("wo", "world") => positive
```

More Utilities
--------------


The [CONCAT](https://support.airkit.com/reference/concat) function will combine two or more strings.



```javascript Airscript
CONCAT("Hello ", "world!") => "Hello world!"  
CONCAT("Hello ", "world", "!") => "Hello world!"  
CONCAT("Hello", " ", "world", "!") => "Hello world!"
```

In order to replace a substring with another use [REPLACE](https://support.airkit.com/reference/replace) or [SUBSTITUTE](https://support.airkit.com/reference/substitute). The [REPLACE](https://support.airkit.com/reference/replace) function will replace the first occurrence of the substring, while the [SUBSTITUTE](https://support.airkit.com/reference/substitute) function will replace any number of occurrences.



```javascript Airscript
REPLACE("Hello world!", "l", "L") => "HeLlo world!"  
SUBSTITUTE("Hello world!", "l", "L") => HeLLo worLd!"
```

Joining and Splitting
---------------------


Another way to combine strings is using the [JOIN](https://support.airkit.com/reference/join) function to combine multiple strings with a particular separator.



```javascript Airscript
JOIN([ "Hello", "world!" ], " ") => "Hello world!"  
JOIN([ "Hello", "world!" ], ", ") => "Hello, world!"
```

The [SPLIT](https://support.airkit.com/reference/split) function is the opposite of the [JOIN](https://support.airkit.com/reference/join) function, in that it turns a string into multiple strings by splitting on a separator.



```javascript Airscript
SPLIT("Hello world!") => [ "Hello", "world!" ]
```

Parsing and Formatting
----------------------


It is very common for external systems to encode different types as strings. Airkit provides a set of functions to convert between other types and strings.




| Function Name | From | To |
| --- | --- | --- |
| [TO_JSON](https://support.airkit.com/reference/to_json) | NULL, Boolean, Number, String, Object List | JSON |
| [FROM_JSON](https://support.airkit.com/reference/from_json) | JSON String | NULL, Boolean, Number, String, Object List |
| [FORMAT_NUMBER](https://support.airkit.com/reference/format_number) | Number | Configurable |
| [PARSE_NUMBER](https://support.airkit.com/reference/parse_number) | Configurable | Number |
| [FORMAT_PHONE](https://support.airkit.com/reference/format_phone) | Phone Number | E-164 String ("+15551234567") |
| [PARSE_PHONE](https://support.airkit.com/reference/parse_phone) | E-164 String ("+15551234567") | Phone Number |
| [FORMAT_DATETIME](https://support.airkit.com/reference/format_datetime) | Datetime | RFC 3339 timestamp (Configurable) |
| [DATETIME_FROM_FORMAT](https://support.airkit.com/reference/datetime_from_format) | RFC 3339 timestamp (Configurable) | Datetime |
| [FORMAT_DATE](https://support.airkit.com/reference/format_date) | Date | RFC 3339 timestamp (Configurable) |
| [DATE_FROM_FORMAT](https://support.airkit.com/reference/date_from_format) | RFC 3339 timestamp (Configurable) | Date |
| [FORMAT_TIME](https://support.airkit.com/reference/format_time) | Time | RFC 3339 timestamp (Configurable) |
| [TIME_FROM_FORMAT](https://support.airkit.com/reference/time_from_format) | RFC 3339 timestamp (Configurable) | Time |


Relevant Functions
------------------


* [SPLIT](https://support.airkit.com/reference/split)
* [SUBSTRING](https://support.airkit.com/reference/substring)
* [LOWERCASE](https://support.airkit.com/reference/lowercase)
* [FORMAT_TIME](https://support.airkit.com/reference/format_time)
* [FORMAT_DATETIME](https://support.airkit.com/reference/format_datetime)
* [FORMAT_DATE](https://support.airkit.com/reference/format_date)
* [ISSTRING](https://support.airkit.com/reference/isstring)
* [LENGTH](https://support.airkit.com/reference/length)
* [CONTAINS](https://support.airkit.com/reference/contains)
* [REPLACE](https://support.airkit.com/reference/replace)
* [SUBSTITUTE](https://support.airkit.com/reference/substitute)
* [PADSTRING](https://support.airkit.com/reference/padstring)
* [CONCAT](https://support.airkit.com/reference/concat)
* [PARSE_NUMBER](https://support.airkit.com/reference/parse_number)
* [UPPERCASE](https://support.airkit.com/reference/uppercase)
* [TO_JSON](https://support.airkit.com/reference/to_json)
* [PARSE_PHONE](https://support.airkit.com/reference/parse_phone)
* [TITLECASE](https://support.airkit.com/reference/titlecase)
* [STRIP](https://support.airkit.com/reference/strip)
* [STRING_COMPARE](https://support.airkit.com/reference/string_compare)
* [REPT](https://support.airkit.com/reference/rept)
* [TRIM](https://support.airkit.com/reference/trim)
* [STRING_FIND](https://support.airkit.com/reference/string_find)
* [FORMAT_NUMBER](https://support.airkit.com/reference/format_number)
* [DATETIME_FROM_FORMAT](https://support.airkit.com/reference/datetime_from_format)
* [DATE_FROM_FORMAT](https://support.airkit.com/reference/date_from_format)
* [TIME_FROM_FORMAT](https://support.airkit.com/reference/time_from_format)
* [PARSE_PHONE](https://support.airkit.com/reference/parse_phone)
* [FORMAT_PHONE](https://support.airkit.com/reference/format_phone)