Airscript is designed to easily facilitate real-world information retrieval and manipulation. In the real world data is messy, doesn’t align with the user interface, and you may not be able to query it like a database. We’ll cover three common operations on data.


* *Filtering*: There are several techniques to search for data.
* *Joining*: Data of one type is often related to data of another. Querying data by those relations is a powerful technique.
* *Transformations*: External systems may represent their data differently from your application. Airscript has built-in features to help transform one representation into another.


There are two primary ways to work with collections of data in Airscript: Path Expressions and [Query Expressions](https://support.airkit.com/docs/filtering-data-using-query-expression). While the same task can often be accomplished with either, they both have complementary strengths and weaknesses. We'll cover how to leverage both to retrieve and manipulate data. Where possible examples with be given in both expression styles.


For the following examples, let us consider that we have two variables, one containing a ```list_of_books``` and another that holds a ```selected_book```.



```javascript Airscript
list_of_books = [
  { 
    title: "Angels & Demons",
    author: "Dan Brown",
    isbn: "9781416524793",
    genres: ["Fiction"]
  },
  {
    title: "The Da Vinci Code",
    author: "Dan Brown",
    isbn: "9780307879257",
    genres: ["Fiction"]
  },
  {
    title: "Hackers: Heroes of the Computer Revolution",
    author: "Steven Levy",
    isbn: "9780141000510",
    genres: ["History"]
  },
  {
    title: "Moonwalking with Einstein: The Art and Science of Remembering Everything",
    author: "Joshua Foer",
    isbn: "9781594202292",
    genres: ["Nonfiction"]
  },
  ...
]
selected_book = {
  title: "Angels & Demons"
  author: "Dan Brown"
  isbn: "9781416524793"
  genres: ["Fiction"]
}
```

Note: Though the techniques in this article are quite useful, if filtering or joining can be done in [Data Operation](https://support.airkit.com/reference/data-operation-overview) it should be done there. The external system will be more performant than doing it in Airscript yourself.


Path Expression
---------------


The most straightforward and common way to work with Lists and Objects is to retrieve a single item by index or field name respectively. For example, in order to retrieve the author of the ```selected_book```, use the following Path Expression



```javascript Airscript
selected_book.author => "Dan Brown"
```

This syntax is valid for any expression, we could perform the same operation on an object literal.



```javascript Airscript
{
 title: "Angels & Demons"
 author: "Dan Brown"
 isbn: "9781416524793"
 genres: ["Fiction"]
}.author => "Dan Brown"
```

While retrieving data from an object requires using a field name, retrieving data from a list uses a number (or index) indicating the position in the list. In order to retrieve the first book from ```list_of_books``` retrieve the item at index **0**.



```javascript Airscript
list_of_books[0] => {
  title: "Angels & Demons"
  author: "Dan Brown"
  isbn: "9781416524793"
  genres: ["Fiction"]
}
```

An important note is that these operations can be chained. To retrieve the author of the first book we first retrieve the first book and then retrieve the author of that book.



```javascript Airscript
list_of_books[0].author => "Dan Brown"
```

And to retrieve the first genre of the first book:



```javascript Airscript
list_of_book[0].genres[0] => "Fiction"
```

### Slicing Lists

Lists can be sliced using the following syntax:

```javascript Airscript
listName[indexFrom:indexTo]
```

For example, if i wanted to get the second and the third book objects from the ```list_of_books```, the following expression should be used:

```javascript Airscript
list_of_books[1:2]
```

Query Expression
----------------


The [Query Expression](https://support.airkit.com/docs/filtering-data-using-query-expression) is quite similar to SQL, or [LINQ](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/). It is used to select multiple values from a collection. The most basic Query Expression does nothing and simply returns the original collection.



```javascript Airscript
FROM book IN list_of_books
SELECT book
=> [
  { 
    title: "Angels & Demons",
    author: "Dan Brown",
    isbn: "9781416524793",
    genres: ["Fiction"]
  },
  {
    title: "The Da Vinci Code",
    author: "Dan Brown",
    isbn: "9780307879257",
    genres: ["Fiction"]
  },
  {
    title: "Hackers: Heroes of the Computer Revolution",
    author: "Steven Levy",
    isbn: "9780141000510",
    genres: ["History"]
  },
  {
    title: "Moonwalking with Einstein: The Art and Science of Remembering Everything",
    author: "Joshua Foer",
    isbn: "9781594202292",
    genres: ["Nonfiction"]
  },
  ...
]
```

This works by creating a variable to be used for each item in the collection, here we assign each book in ```list_of_books``` to the variable ```book.``` The Query Expression will evaluate the ```SELECT``` clause for each book in ```list_of_books``` and return a new list with the result of the ```SELECT``` clause**.** While the last expression is simple, it is also rather useless. Query Expressions can do much more interesting things. We can retrieve a list of the ISBNs by modifying the ```SELECT``` clause to return each book’s ISBN.



```javascript Airscript
FROM book IN list_of_books
SELECT book.isbn
=> [
  "9781416524793",
  "9781416524793",
  "9781594202292",
  "9780141000510",
  ...
]
```

Perhaps we would like to order the books alphabetically by author, we can do so by including an ```ORBER BY``` clause



```javascript Airscript
FROM book IN list_of_books
ORDER BY book.author
SELECT book
=> [
  { 
    title: "Angels & Demons",
    author: "Dan Brown",
    isbn: "9781416524793",
    genres: ["Fiction"]
  },
  {
    title: "The Da Vinci Code",
    author: "Dan Brown",
    isbn: "9780307879257",
    genres: ["Fiction"]
  },
  {
    title: "Moonwalking with Einstein: The Art and Science of Remembering Everything",
    author: "Joshua Foer",
    isbn: "9781594202292",
    genres: ["Nonfiction"]
  },
  {
    title: "Hackers: Heroes of the Computer Revolution",
    author: "Steven Levy",
    isbn: "9780141000510",
    genres: ["History"]
  },
  ...
]
```

Using the ```LIMIT``` clause we could select just the first two books.



```javascript Airscript
FROM book IN list_of_books
LIMIT 2
SELECT book
=> [
  { 
    title: "Angels & Demons",
    author: "Dan Brown",
    isbn: "9781416524793",
    genres: ["Fiction"]
  },
  {
    title: "The Da Vinci Code",
    author: "Dan Brown",
    isbn: "9780307879257",
    genres: ["Fiction"]
  }
]
```

Note that in the last examples the ```SELECT``` clause didn’t do much other than simply selecting each item. In these cases, the ```SELECT``` clause can be omitted.



```javascript Airscript
FROM book IN list_of_books LIMIT 2
```

Filtering
---------


It is often necessary to search through a data set for a particular item or set of items. If we would like to search the ```list_of_books``` by a specific author, we could use a Query Expression with a ```WHERE``` clause requiring that the author field of the book be equal to ```“Dan Brown”```.



```javascript Airscript
FROM book IN list_of_books
WHERE book.author = "Dan Brown"
SELECT book
=> [
  { 
    title: "Angels & Demons"
    author: "Dan Brown"
    isbn: "9781416524793"
    genres: ["Fiction"]
  },
  {
    title: "The Da Vinci Code",
    author: "Dan Brown",
    isbn: "9780307879257",
    genres: ["Fiction"]
  }
]
```

The equivalent Path Expression returns the same result and looks like this:



```javascript Airscript
list_of_books[?(@.author = "Dan Brown")]
```

There are often queries that are only intended to return a single result. For example, assuming ```list_of_books``` does not contain duplicates searching for a book by ISBN will only have one result. To access this singular book directly we can filter based on books that have a matching ISBN. Since there should only be one, we can simply take the first element of the resulting list.



```javascript Airscript

 FROM book IN list_of_books
 WHERE book.isbn = "9781416524793"
 SELECT book[0]
=> { 
  title: "Angels & Demons",
  author: "Dan Brown",
  isbn: "9781416524793",
  genres: ["Fiction"]
}
```

The equivalent Path Expression:



```javascript Airscript
list_of_books[?(@.isbn = "9781416524793")][0]
```

Note that if no book is found, the result of these expressions will return **[NULL](https://support.airkit.com/reference/the-null-data-type).**


In addition to removing items from the collection, Airscript also makes it quite convenient to work with nested data. Notice that if we wanted to search by genre we could not do the same thing because each book can have more than one genre. Rather than using the equality operator, we can use the [CONTAINS](https://support.airkit.com/reference/contains) function to determine if the list of genres contains the genre we are looking for.



```javascript Airscript
FROM book IN list_of_books
WHERE CONTAINS(book.genres, "Non-fiction")
SELECT book
=> [
  { 
    title: "Angels & Demons"
    author: "Dan Brown"
    isbn: "9781416524793"
    genres: ["Fiction"]
  },
  {
    title: "The Da Vinci Code",
    author: "Dan Brown",
    isbn: "9780307879257",
    genres: ["Fiction"]
  }
]
```

And the equivalent Path Expression



```javascript Airscript
list_of_books[?(CONTAINS(@.genres, "Non-fiction"))]
```

The concept of filtering can still be pushed further. Suppose we would like to retrieve a list of all the genres our ```list_of_books``` covers. We could begin by retrieving the list of genres from each book using the techniques we have seen so far. The Query Expression is fairly straightforward.



```javascript Airscript
FROM books IN list_of_books
SELECT book.genres
```

The following Path Expression will return the same result.



```javascript Airscript
list_of_books[*].genres
```

However, this gives us a list of lists of genres



```javascript Airscript
[
  ["Fiction"]
  ["Fiction"]
  ["History"]
  ["Nonfiction"]
  ...
]
```

Using the [FLAT](https://support.airkit.com/reference/flat) function we can convert this double list into a single list.



```javascript Airscript
FLAT(list_of_books[*].genres)
=>
[
  "Fiction"
  "Fiction"
  "History"
  "Nonfiction"
  ...
] "
```

Finally, notice that we have duplicates. We can remove the duplicates using the ```DISTINCT``` keyword of a Query Expression



```javascript Airscript
FROM genre
IN FLAT(FROM book IN list_of_books SELECT book.genres)
SELECT DISTINCT genre**=> ["Fiction", "History", "Nonfiction", ...]
```

Note that there is no equivalent Path Expression to a ```DISTINCT``` Query Expression, however, we are free to mix and match either type of expression.



```javascript Airscript
FROM genre IN FLAT(list_of_books[*].genres)
SELECT DISTINCT genre
=> ["Fiction", "History", "Nonfiction", ...]
```

Joining
-------


The next technique we will discuss is useful when relating one data set to another. We would like to add a Web Page to our application that shows the user the distinct list of genres we just collected with a description of each genre. For the following example assume we have a variable named ```list_of_genres``` that contains a list of genre objects that contain a name and a description.



```javascript Airscript
list_of_genres = [
  {
    name: "Fiction",
    description: "..."
  },
  {
    name: "History",
    description: "...",
  },
  {
    name: "Nonfiction",
    description: "...",
  },
  {
    name: "Mystery",
    description: "...",
  }
```

We begin by using our previous expression to extract the distinct genre names from ```list_of_books.``` Rather than selecting the genre name itself, we instead filter ```list_of_genres``` by each distinct genre and return the genre that was found.



```javascript Airscript
FROM genre_name IN FLAT(list_of_books[*].genres)
SELECT DISTINCT (  
 FROM genre IN list_of_genres
 WHERE genre.name = genre_name
 SELECT genre  
)[0]
=> [
  {
    name: "Fiction",
    description: "..."
  },
  {
    name: "History",
    description: "...",
  },
  {
    name: "Nonfiction",
    description: "...",
  }
]
```

The equivalent Path Expression



```javascript Airscript
FROM genre IN FLAT(list_of_books[*].genres)
SELECT DISTINCT list_of_genres[?(@.name = genre_name)][0]
=> [
  {
    name: "Fiction",
    description: "..."
  },
  {
    name: "History",
    description: "...",
  },
  {
    name: "Nonfiction",
    description: "...",
  }
]
```

Transformations
---------------


When querying or sending data to an external system the way you represent data may not be the same as the way an external system represents data. For example, imagine there is a service that will return book information given a list of ISBNs. However, this external system requires each ISBN to be prefixed with the string ```“ISBN:”```. In order to send ```list_of_books``` we must not only extract the ISBN but also add the required prefix turning ```“9781416524793”``` into ```“ISBN:9781416524793”```. Since ```SELECT``` clauses are just Airscript expressions we can use the [CONCAT](https://support.airkit.com/reference/concat) function to do this.



```javascript Airscript
FROM book IN list_of_books
SELECT CONCAT("ISBN:", book.isbn)
=> [   
  "ISBN:9781416524793",   
  "ISBN:9781416524793",   
  "ISBN:9781594202292",   
  "ISBN:9780141000510",   
  ...  
]
```

As we have seen we can retrieve a book with a specific ISBN by filtering our list to only the book with the matching ISBN, and then selecting the first element in that list.



```javascript Airscript
FROM book IN list_of_books WHERE book.isbn = "9781416524793")[0]=> {   
  title: "Angels & Demons",  
  author: "Dan Brown",  
  isbn: "9781416524793",   
  genres: ["Fiction"]   
}
```


```javascript Airscript
list_of_books[?(@.isbn = "9781416524793")][0]
```

If our application has to do this often it could get tedious. If we were to create an object where the fields of the object were the ISBNs themselves we could use a simple Path Expression to retrieve the book by ISBN directly without having to filter.



```javascript Airscript
books_by_isbn["9781416524793"]
```

The Query Expression has one more feature we haven’t explored yet. In addition to creating lists, it can also be used to create objects. In order to do so rather than an expression in the ```SELECT``` clause use a **key: value** pair just as you would when specifying the properties of an object.



```javascript Airscript
FROM book IN list_of_books
SELECT "{{book.isbn}}": book
```

Note: If you were to create a variable of this type, you would choose [The Any (JSON) Variable Data Type](https://support.airkit.com/reference/the-any-json-variable-data-type). You cannot create an [App Object](https://support.airkit.com/docs/airdata-app-objects) for this variable because the field names cannot be known in advance.