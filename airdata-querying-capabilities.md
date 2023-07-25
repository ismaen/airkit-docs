AirData is a system of record that Airkit provides. There are a number of built in methods available that allow you to interact with entries in the datastore such as **QUERY**, **PUT**, **DELETE**, **INSERT**, and **PATCH**. We’ll focus here on the **QUERY** method and how you can use built in filtering to hone in on your data.


![os-querying-1.gif](./assets_v1714/airdata-querying-capabilities-v1714-0.gif)


For the following examples, let’s say we have a sample App Object in our Datastore called Dog. Each Dog entry has the following schema:



```json Airscript
{
  "name": "Text",
  "Nicknames": "List<Text>",
  "breed": "Text",
  "age": "Integer",
  "owner": "Text",
  "isTrained": "Boolean"
}
```

Example data:



```json Airscript
{
  "name": "Goofy",
  "nicknames": [
    "goofy",
    "goofball"
  ],
  "breed": "pug",
  "age": 7,
  "owner": "Reyna",
  "isTrained": true
}
```

Let’s use this sample Datastore below with nine Dog entries and explore some of the filters available to query the Datastore.![os-querying-1.png](./assets_v1714/airdata-querying-capabilities-v1714-1.png)


Below are the specifications of all the available per-field filters, grouped by categorical type of search. For AirData querying, the documentation format is used as such:


*filterKeyWord*: the primary name for the filter.


*type*: the Airkit data type of the field that you wish to query (text, list of texts, etc)


*aliases*: can be used to clarify the intent of or shorten your query using different filter key words.

 For example, the following queries will operate identically:

```javascript Airscript
{ "age": { "<": 2 } }
```

```javascript Airscript
{ "age": { "lessThan": 2 } }
```

*example query*: A valid sample query based on the example datastore.


*query returns*: A description of what the sample query would return from example datastore.


### String matching filters


* **anyOf**

    + type: **T | Collection<T>** where **T** = type of field
    + aliases: **=**, **in**, **any**, **eq**
    + description: strict equality test
    + example query: **{ "breed": { "anyOf": ["mutt" , "pug"] } }**
        - query returns: All dogs exactly matching the string "mutt" or "pug" in the "breed" field.


* **insensitiveAnyOf**

    + type: **T | Collection<T>** where **T** = type of field
    + aliases: **~=**, **ieq**, **iEquals**, **insensitiveEquals**, **iAnyOf**
    + description: when **T** is Text, case-insensitive equality; when **T** is **List**, unordered equality; otherwise defaults to anyOf behavior
    + example query: **{ "name": { "insensitiveAnyOf": ["DAISY" , "PENNY"] } }**
        - query returns: All dogs with names matching the string "daisy" or "penny" regardless of capitalization


* **noneOf**

    + type: **T | Collection<T>** where **T** = type of field
    + aliases: **!=**, **not**, **none**, **neq**, **!eq**
    + description: strict inequality test
    + example query: **{ "owner": { "noneOf": ["Damon", "Jeff"] } }**
         - query returns: All dogs who have an owner that is NOT "Damon" or "Jeff".


* **like**

    + type: **Text**
        - field type must be TextType
    + description: string contains, only works on text fields
    + example query: **{ "name": { "like": "y" } }**
        - query returns: Any dog that has the character "y" in their name.


### Quantitative filters


* **lessThan**

    + type: **T** where **T** = type of field
    + aliases: **<**, **lt**
    + description: less than, exclusive
    + example query: **{ "age": { "lessThan": "5" } }**
        - query returns: All dogs who are less than 5 years old.


* **lessThanOrEqual**

    + type: **T** where **T** = type of field
    + aliases: **<=**, **lte**
    + description: less than, inclusive
    + example query: **{ "age": { "lessThanOrEqual": "5" } }**
        - query returns: All dogs who are strictly younger than 5 years old.


* **greaterThan**

    + type: **T** where **T** = type of field
    + aliases: **>**, **gt**
    + description: greater than, exclusive
    + example query: **{ "age": { "greaterThan": "2" } }**
        - query returns: All dogs who are strictly older than 2 years.


* **greaterThanOrEqual**

    + type: **T** where **T** = type of field
    + aliases: **>=**, **gte**
    + description: greater than, inclusive
    + example query: **{ "age": { "greaterThanOrEqual": "10" } }**
        - query returns: All dogs who are at least 10 years old or older.


### List/set filters


* **intersects**

    + type: **Set<T>** where **T** = type of element type in **List<T>**
    + field type must be List
    + aliases: ∩, intersect, intersection, intersectionOf
    + description: matches where any of the elements in the filter also exist in the list
    + example query: **{ "nicknames": { "intersects": [ "dog", "doggy", "Lulu", "doesn’t matter" ] } }**
        - query returns: Any entry that has a nickname in the searched array. In our example, it returns entries 2,3,6 & 7.


* **supersetOf**

    + type: **Set<T> | Set<Set<T>>** where **T** = type of element type in **List<T>**
        - field type must be List
    + aliases: ⊇, superset, overlap, overlaps, overlapsAny, supersetOfAny
    + description: matches where the field is a superset of any of the provided sets
    + example query: **{ "nicknames": { "supersetOf": [ "doggy", "dog" ] } }**
        - query returns: Any dog where the field is a superset of the array in the query. In our example, it’d only return entry 3.


* **subsetOf**

    + type: **Set<T> | Set<Set<T>>** where **T** = type of element type in **List<T>**
        - field type must be List
    + aliases: ⊆, subset, overlapped, subsetOfAny, overlappedBy
    + description: matches where the field is a subset of any of the provided sets
    + example query: **{ "nicknames": { "subsetOf": [ "pugsy", "doggy", "doodle", "dais" ] } }**
         - query returns: Any dog whose nicknames are a subset of the list searched. In our example, it’s return entries 6,7, & 8


* **containsAnyOf**
    + type: **Set<T> | Text** where **T** = type of element type in **List<T>**
        - field type must be **List | Text**
    + aliases: **∈**, **containsAny**
    + description: if field is list, matches if any element in this set exists in the field if text, matches if any of the strings are a substring of the field
    + example query 1: **{ "nicknames": { "containsAnyOf": [ "dais", "harry" ] } }**
        - query returns: Any dog who has any of the following nicknames. Our example will only return entries 8 & 9.
    + example query 2: **{ "nicknames": { "containsAnyOf": "pugsy" } }**
        - query returns: Iterates over the list and chs to see if query value is present as a substring in the list. Our example returns entries 4 & 9


* **containsAllOf**

    + type: **Set<T> | Text** where T = type of element type in **List<T>**
        - field type must be **List | Text**
    + aliases: **containsAll**
    + description: if field is list, matches if all elements in this set exist in the field if text, matches if all of the strings are a substring of the field
    + example query: **{ "nicknames": { "containsAllOf": [ "doggy", "dog" ] } }**
        - query returns: Any dog who has all of the following nicknames, but can have others as well. Our example only returns entry 3.


* **containsNoneOf**
    + type: **Set<T> | Text** where **T** = type of element type in **List<T>**	
        - field type must be **List | Text**
    + aliases: **∉**, **containsNone**
    + description: if field is list, matches if none of the elements in this set exist in the field if text, matches if none of the strings are a substring of the field
    + example query: **{ "nicknames": { "containsNoneOf": [ "doggy" ] } }**
         - query returns: Any dog who does not have the nickname "doggy". Our example returns 1,2,4,5,8, & 9.


Examples
-------------------


You can use [Airscript](https://support.airkit.com/docs/airscript-quick-start) to further refine your search. For example: 

```javascript Airscript
{ "dogName": { "anyOf": "{{ LOWERCASE("LUCY")}}" } }
```

You can combine multiple queries to specify your search. 

```javascript Airscript
{ "dogName": { "insensitiveAnyOf": "daisy" }, "dogAge": { "greaterThan": 4 } }
```
[block:callout]
{
  "type": "info",
  "body": "Note: Comma delimited queries function as an AND operation, not OR."
}
[/block]