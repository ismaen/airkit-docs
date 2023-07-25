Airscript supports arithmetic on numbers and provides a large library of functions for dealing with numbers..


* [MAX](https://support.airkit.com/reference/max) - Returns the largest number of a list of numbers
* [MIN](https://support.airkit.com/reference/min) - Returns the smallest number from a list of numbers
* [ABS](https://support.airkit.com/reference/abs) - Returns the absolute value of a number
* [ROUND](https://support.airkit.com/reference/round) - Rounds a number
* [FLOOR](https://support.airkit.com/reference/floor) - Returns the integer at or below a number (**1.1** becomes **1)**
* [CEILING](https://support.airkit.com/reference/ceiling) - Returns the integer at or above a number (**1.1** becomes **2)**
* [PI](https://support.airkit.com/reference/pi) - Returns the constant π
* [RANDOM](https://support.airkit.com/reference/random) - Returns a random number


Displaying Numbers in Text
--------------------------


When displaying a number such as **100001** it is more readable to the user to denote where the thousands place is. In the United States, there will be a comma to denote the thousandth's place: 100,001. However, in Europe, there will be a period to denote the thousandth's place: 100.001. Displaying a number with the wrong formatting for your user can cause confusion. The [FORMAT_NUMBER](https://support.airkit.com/reference/format_number) number function will convert a number into a string with a given format. To display a number using thousandths separators use the format string **","**, the correct locale will be selected for the user by default.



```javascript Airscript
FORMAT_NUMBER(100001, ",") => "100,001"
```

When displaying decimal numbers there are two options, fixed precision, or significant digits. Fixed precision will always display the same number of digits after the decimal point.



```javascript Airscript
FORMAT_NUMBER(100001, ".2f") => "100001.00"  
FORMAT_NUMBER(3.1459, ".2f") => "3.14"
```

To format a number using significant digits omit the *f* in the format string.



```javascript Airscript
FORMAT_NUMBER(100001, "") => "1e+5"  
FORMAT_NUMBER(3.1459, ".2") => "3.1"
```

Thousandths separators can be combined with precision.



```javascript Airscript
FORMAT_NUMBER(100001, ",.2f") => "100,001.00"
```

Finally, there are occasions where a number should not be formatted at all, these cases usually involve a number that is meant to be read by a computer or external system. Use an empty string for these cases.



```javascript Airscript
FORMAT_NUMBER(100001, "") => "100001"
```

Parsing Numbers from Text
-------------------------


To parse a number from a string use the [PARSE_NUMBER](https://support.airkit.com/reference/parse_number) function.



```javascript Airscript
PARSE_NUMBER("100,001") => 100001  
PARSE_NUMBER("3.14159") => 3.14159
```

Working with Currency
---------------------


While currency is measured using a number, it also requires a unit. One U.S. dollar (**"USD"**) is different from one Canadian dollar (**"CAD"**)



```javascript Airscript
CURRENCY(1, "USD", 0)  
CURRENCY(1, "CAD", 0)
```

However, one U.S. dollar is the same as one-hundred U.S. pennies.



```javascript Airscript
CURRENCY(1, "USD", 0)  
CURRENCY(100, "USD", 2)
```

To represent this, in addition to an **amount**, the [Currency](https://support.airkit.com/reference/currency) type has a **code** that represents which currency it is (U.S. vs Canadian dollars), and a precision to represent the denomination (dollars vs pennies).


It is important to pick the smallest denomination possible for a given currency because when working with decimal numbers small errors can be introduced. For this reason, when working with **"USD"** it is recommended to use at least a precision of **2** to represent pennies to avoid having to use decimal numbers like **0.01**.


When displaying a currency to a user use the [FORMAT_CURRENCY](https://support.airkit.com/reference/format_currency) function, it will create a string that displays the currency to the user while taking into account the user's locale. For a user with a U.S. locale



```javascript Airscript
FORMAT_CURRENCY(one_hundred_us_pennies) => "$1.00"
```

while for a user with a Canadian locale



```javascript Airscript
FORMAT_CURRENCY(one_hundred_us_pennies) => "US$1.00"
```

The [PARSE_CURRENCY](https://support.airkit.com/reference/parse_currency) function will go in the opposite direction, it will parse a string like **"$1.00"** into a currency representing **100** cents.


### Number Examples


Functions in this Article
-------------------------


* [MAX](https://support.airkit.com/reference/max) - Returns the largest number of a list of numbers
* [MIN](https://support.airkit.com/reference/min) - Returns the smallest number from a list of numbers
* [ABS](https://support.airkit.com/reference/abs) - Returns the absolute value of a number
* [ROUND](https://support.airkit.com/reference/round) - Rounds a number
* [FLOOR](https://support.airkit.com/reference/floor) - Returns the integer at or below a number (**1.1** becomes **1)**
* [CEILING](https://support.airkit.com/reference/ceiling) - Returns the integer at or above a number (**1.1** becomes **2)**
* [PI](https://support.airkit.com/reference/pi) - Returns the constant π
* [RANDOM](https://support.airkit.com/reference/random) - Returns a random number
* [PARSE_NUMBER](https://support.airkit.com/reference/parse_number) - Parses a number from a string
* [FORMAT_NUMBER](https://support.airkit.com/reference/format_number) - Formats a number into a string
* [FORMAT_CURRENCY](https://support.airkit.com/reference/format_currency) - Converts a currency to a string
* [PARSE_CURRENCY](https://support.airkit.com/reference/parse_currency) - Converts a string into a currency