Airscript includes a Query Expression syntax that allows you to operate on lists of items. This syntax looks somewhat similar to SQL but is based on a concept called Language Integrated Query.


Using this syntax you can filter or map a list of items.


The general syntax looks like the following:



```javascript Airscript
FROM
  item
IN
  collection
WHERE
  item.score > 80
SELECT
  item

```

FROM item IN [{score: 100}, {score: 20}, {score: 40}, {score: 85}] WHERE item.score > 80 SELECT item
In this simple example we go through a collection and filter out all items that have a score property greater than 80.


The following example shows one way to nest a Query Expression within a Query Expression.



```javascript Airscript
FROM
  qualifiedPerson
IN
  FROM
    person
  IN
    collectionOfPoeple
  WHERE
    person.qualified = true
  SELECT
    person
WHERE
  qualifiedPerson.score > 80
SELECT
  qualifiedPerson

```

In this example we are pulling only qualified people out of a collection of people and then looking for people in that collection that have a score greater than 80.


Any valid Airscript function is valid within our syntax. For example, below we use the Airscript [STRING_FIND](https://support.airkit.com/reference/string_find) in the WHERE clause.



```javascript Airscript
FROM
  p
IN
  persons
WHERE
  STRING_FIND(p.name, "Bob") >= 0
SELECT
  p.name

```

This example is going through all persons and finding all persons who have a name that contains Bob in it. Then we are returning the name of those persons. This will return as a list of **p.name**


While this is the basic example of our syntax here, we have even more functionality baked into our syntax. The supported technical arguments are:



```javascript Airscript
FROM
    itemBinding = identifier,
  [ indexBinding = identifier, [ collectionBinding = identifier ] ]
IN
    expression
[WHERE expression]
[ORDER BY expression direction = (ASCENDING | DESCENDING)]
[LIMIT expression [OFFSET expression]]
SELECT [DISTINCT] selectExpression

```

Anything in brackets ([]) means that it is optional. We do not need to have a WHERE clause. There are also ORDER BY clause and LIMIT options. If you want your result to return only unique items you can put the DISTINCT modifier on your select and you receive a SET with duplicate items removed.


One other important note: there is an index binding, meaning that you can also get the index of the item you are at in your iteration. For example:



```javascript Airscript
FROM
  item, index
IN
  [{"foo": "bar"}, {"foo": "baz"}]
SELECT
  {"{{index}}": item}

```

FROM item, index IN [{"foo": "bar"}, {"foo": "baz"}] SELECT {"{{index}}": item}
In this case, index is a special reserved word that you put at the end of your expression and you can then refer to it in the rest of your statement. The result will be: 



```javascript Airscript
[
  {
    "0": {
      "foo": "bar"
    }
  },
  {
    "1": {
      "foo": "baz"
    }
  }
]

```