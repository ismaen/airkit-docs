There are times when data may not have a value. For example, in an application that is designed to capture a user's address the variable holding the address will be empty until the user has filled in their address. Another example may be a user that doesn't have a middle name. Variables must always have a value, so [The Null Data Type](https://support.airkit.com/reference/the-null-data-type) is used to indicate that a certain piece of data is missing.


If you were to store the address a user enters in a variable called ```address``` and access that variable before the user has entered their address you would end up with the value ```NULL.```



```javascript Airscript
address => NULL
```

Taking this example a bit further, if you were to access a property from the address such as ```zip_code``` you would also end up with the value ```NULL.```



```javascript Airscript
address.zip_code => NULL
```

If some of your data may be missing, it is a good idea to check if it is ```NULL``` before using it. For example, if you wanted to display the ```zip_code``` field to the user and there is no value it would be better to display a helpful message instead.



```javascript Airscript
IF(address.zip_code = NULL, "Zip code unknown.", address.zip_code)
```

Working with Empty Values
-------------------------


In the previous example, what would you display if the ```zip_code``` is the empty string (```""```)?. Well, we could of course also check for that.



```javascript Airscript
IF(  
  address.zip_code = NULL OR address.zip = "",  
  "Zip code unknown.",  
  address.zip_code  
)
```

However, it is much more convenient to use the [ISEMPTY](https://support.airkit.com/reference/isempty) function, which returns ```FALSE``` for both ```""```, as well as ```NULL```.



```javascript Airscript
IF(ISEMPTY(address.zip_code), "Zip code unknown.", address.zip_code)
```

There is a companion [ISNOTEMPTY](https://support.airkit.com/reference/isnotempty) function, so we could accomplish the same by changing the ordering.



```javascript Airscript
IF(ISNOTEMPTY(address.zip_code), address.zip_code, "Zip code unknown.")
```

This situation is not unique to strings, you may want to handle an empty list the same way you treat ```NULL```. The following values are considered to be empty.


* The null value: ```NULL```
* An empty list: ```[]```
* An empty object: ```{}```
* An empty string: ```""```


Working with Values that are Considered Falsy
---------------------------------------------


The [IF](https://support.airkit.com/reference/if) function, the **WHERE** clause of the [Query Expression](https://support.airkit.com/docs/filtering-data-using-query-expression), and the filtering Path Bindings all examine their values in terms of whether they are falsy or not. For example, the empty string (```""```) is falsy, so we did not need to use they [ISNOTEMPTY](https://support.airkit.com/reference/isnotempty) function at all in our previous example.



```javascript Airscript
IF(address.zip_code, address.zip_code, "Zip code unknown")
```

The following values are considered falsey


Working with Values of an Unknown Type
--------------------------------------


You may not always know that a value will be of a certain type. For example, even though you asked the user to enter a phone number, they may have entered something else like ```"Hello Airkit!"```. Not only, can you not call a phone number like ```"Hello Airkit"```, a phone number must be in a very specific format in order to be called (or sent an SMS). The [ISPHONE](https://support.airkit.com/reference/isphone) function will return ```TRUE``` when a string represents a phone number that can be called. 


Several types have a corresponding function that tells you whether or not a value is of that type.


* [ISSTRING](https://support.airkit.com/reference/isstring)
* [ISNUMBER](https://support.airkit.com/reference/isnumber)
* [ISPHONE](https://support.airkit.com/reference/isphone)
* [ISEMAIL](https://support.airkit.com/reference/isemail)


Relevant Functions
------------------


* [IF](https://support.airkit.com/reference/if)
* [ISPHONE](https://support.airkit.com/reference/isphone)
* [ISEMAIL](https://support.airkit.com/reference/isemail)
* [ISSTRING](https://support.airkit.com/reference/isstring)
* [ISNUMBER](https://support.airkit.com/reference/isnumber)
* [ISEMPTY](https://support.airkit.com/reference/isempty)
* [ISNOTEMPTY](https://support.airkit.com/reference/isnotempty)