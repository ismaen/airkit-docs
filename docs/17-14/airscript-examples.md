Creating a timed event
----------------------


Sometimes you need to project time out into the future. When scheduling an event and you want to specify a time, Airscript can help you do that through the date functions.


For example to get a get a time two days from now, we could write the following Airscript:



```javascript Airscript
ADD_TO_DATETIME(
  NOW(),
  2,
  "days"
)
```

In this example we are taking the current time with NOW() adding 2 as number value and "days" as the unit value.


Conditional display of an element
---------------------------------


Imagine you have a form where you only want to display an additional item if a condition is TRUE.


On most elements in the app builder there is a Visible option.


![airscriptExample1.png](https://a01-support.airkit.com/airscript-examples/airscriptExample1.png)


Sometimes you will want to want to do something more than a TRUE or FALSE. In this expression block you can do a bunch of different things.


For example, lets say you have a field you only want to display for persons named "Bob", you could write the following Airscript:



```javascript Airscript
STRING_COMPARE(name, "Bob") = 0
```

This is checking to see if the name is Bob. STRING_COMPARE() takes in two strings and returns a number. If the strings are equal the number is 0.


Another example may be if you have a list of books and you want to display a message to the user if there are no books selected. Here would be the Airscript to check



```javascript Airscript
ISNOTEMPTY(
  selectedBooks
)
```

The function ISNOTEMPTY() takes one parameter and checks to see if it is empty, if so it returns FALSE, Otherwise it returns TRUE.


Here are several other ways you could do the same check:



```javascript Airscript
NOT(ISEMPTY(selectedBooks))
// OR
LENGTH(selectedBooks) < 1

```

Remember that the check is for Visible. If the expression evaluates to TRUE, the element will be visible. If it evaluates to FALSE, it will be hidden.


Formatting a dollar amount
--------------------------


Another common use case is taking a number amount and formatting it for a user to read. It makes sense to keep the numbers in a number format in App Objects for various math operations. Still reading 10000000000 is harder than reading 10,000,000,000. Other countries even use different separators. Luckily Airscript has a FORMAT_CURRENCY() function. You use it like this:



```javascript Airscript
FORMAT_CURRENCY(
  10000000000,
  "USD"
)
```

In this case "USD" is the currency string. You will get \$10,000,000,000.00 out.


Combining a name for a label
----------------------------


Another common example is combining text variables together. Imagine a case where you have an input with three text inputs, one for first name, middle name, and last name. You want to display them combined at the end.


![airscriptExample2.png](https://a01-support.airkit.com/airscript-examples/airscriptExample2.png)


In order to get out the full name, you can use escape characters in your string to display each part of the name:



```javascript Airscript
"{{}}"
```

In Airscript Strings {{ }} are known as escape tokens. Inside the escape tokens you have access to Airscript accessible variables and functions.


There are a couple of other ways to do this. For example:



```javascript Airscript
JOIN(
  [ first_name, middle_name, last_name ],
  " "
)
```

In this example we create an array with the variables and use the JOIN() function to combine them with a space.