Airscript is the programming language provided by Airkit. It is designed to be a simple, but powerful programming language with a focus on data manipulation. It's by strategically combining Airscript with input from app users (or other [external sources](https://support.airkit.com/docs/connecting-to-external-systems), such as an external API) that you control the order, flow, and nature of the interactions between your Airkit apps and the outside world. Most commonly, this is done by [defining a variable](https://support.airkit.com/reference/the-set-variable-action) with Airscript or by using Airscript to access or modify data via the [Transform Data Operation](https://support.airkit.com/reference/the-transform-data-operation), both of which parse any input in Airscript by default.


For a deeper dive into how to try out some Airscript expressions, check out [Testing Airscript Expressions](https://support.airkit.com/docs/testing-airscript-expressions).


Functions
---------


Like most programming languages, Airscript makes extensive use of functions. You can find an alphabetical listing of the functions that Airscript supports on the [Airscript Functions](https://support.airkit.com/docs/testing-airscript-expressions) page.


Arithmetic Operators
--------------------


Airscript supports the standard arithmetic operators: addition (**+**), subtraction (**-**), multiplication (*****) , and division (**/**), as well as remainder (**%**).


Comparison Operators
--------------------


### Equality


Airscript has a number of comparison operators. The equality operator (**=**), returns **TRUE** when two values are the same, and **FALSE** when they are not the same value. For example consider the following expressions:



```javascript Airscript
2 = 2 => TRUE  
2 = 1 => FALSE  
"Airscript" = "Airscript" => TRUE  
"Airscript" = "airscript" => FALSE
```

Comparing two values of different type will always be **FALSE**, for example:



```javascript Airscript
2 = "Airscript" => FALSE
```

It is important to be careful when comparing two complex values such as Objects, Lists, Dates, Times, Datetimes, and **NULL**. The result will only be **TRUE** if the two values are exactly the same rather than just similar. For example


### Inequality


In addition to the equality operator Airscript also supports an inequality operator which is the opposite of the equality operator. The inequality operator can be accessed by the symbol **<>** as well as the symbol **!=**. To understand the inequality operator consider the opposite of our previous examples.



```javascript Airscript
2 <> 2 => FALSE  
2 != 2 => FALSE  
2 <> 1 => TRUE  
2 != 1 => TRUE  
"Airscript" <> "Airscript" => FALSE  
"Airscript" != "Airscript" => FALSE  
"Airscript" <> "airscript" => TRUE  
"Airscript" != "airscript" => TRUE  
2 <> "Airscript" => TRUE  
2 != "Airscript" => TRUE
```

### Ordering


Airscript supports the following ordering operators: greater than (**>**), greater than or equal (**>=**), less than (**<**), less than or equal (**<=**). The ordering operators can be used with Numbers and Strings. For numbers these operators compare the magnitude of the number. Consider the following examples:



```javascript Airscript
1 < 2 => TRUE  
1 <= 2 => TRUE  
1 < 1 => FALSE  
1 <= 1 => TRUE  
1 > 2 => FALSE  
1 >= 2 => FALSE  
1 > 1 => FALSE  
1 >= 1 => TRUE
```

The ordering operators compare Strings lexicographically, consider the following examples:



```javascript Airscript
"air" < "airscript" => TRUE  
"air" <= "airscript" => TRUE  
"airscript" < "airscript" => FALSE  
"airscript" <= "airscript" => TRUE  
"air" > "airscript" => FALSE  
"air" >= "airscript" => FALSE  
"airscript" > "airscript" => FALSE  
"airscript" >= "airscript" => TRUE
```

Comparing the order between two complex objects will always return **FALSE**.


Accessing Data within Collections
---------------------------------


### Object Property Access


Objects are a data type that relates field names to values. For example, an address in the United States is typically made up of a Street, City, State, and Zipcode. In Arikit an example of an Object holding such data might look like this:



```javascript Airscript
{  
  street: "200 California Ave.",  
  city: "Palo Alto",  
  state: "CA",  
  zip: "94036"  
}
```

In order to access the **street** property, one would use dot notation:



```javascript Airscript
({  
  street: "200 California Ave.",  
  city: "Palo Alto",  
  state: "CA",  
  zip: "94036"  
}).street
```

or, if the Object were stored in a variable named **address**:



```javascript Airscript
address.street
```

### List Access


Lists are a data type that store data in a particular order. Imagine we have a list of book titles, in Airscript it might look like this:



```javascript Airscript
[  
  "The Little Schemer",  
  "The Seasoned Schemer",  
  "The Reasoned Schemer",  
  "The Little Prover",  
  "The Little Typer"  
]
```

A particular item can be accessed from a list by its numerical index in the list. Indices begin at the number zero, in other words, the first item in the list is accessed at index **0**. In order to retrieve the book title "The Little Schemer" from our example you would do so like this:



```javascript Airscript
[  
  "The Little Schemer",  
  "The Seasoned Schemer",  
  "The Reasoned Schemer",  
  "The Little Prover",  
  "The Little Typer"  
][0]
```

or, if the list were stored in a variable named **books**:

```json Airscript
books[0]
```


Creating Custom Airscript Functions
-----------------------------------


Custom Airscript functions, defined in terms of established Airscript operators, can be defined in the [Connection Builder](https://support.airkit.com/docs/connection-builder). For a deeper diving into User Defined Functions, check out [this article](https://support.airkit.com/docs/user-defined-functions).