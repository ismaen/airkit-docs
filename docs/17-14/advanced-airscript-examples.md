Formatting a Date
-----------------


Depending on your use case, you might want to display dates differently to your user. Sometimes you want to display a shortened, numerical interpretation, other times you may need to include the full date and time. Airscript provides you tools to configure that, regardless of your needs. You can also combine different date functions together. Here is an example:



```javascript Airscript
FORMAT_DATETIME(
  ADD_TO_DATETIME(
    NOW(),
    2,
    "days"
  ),
  "mm/dd/yyyy"
)
```

Given today’s date (May 20th, 2020) this would result in:


05/20/2020


For more details on how to use the above expressions, check out our previous Airscript Examples, along with looking at the reference material for the Date Functions.


Conditional Expressions
-----------------------


Conditional expressions in Airscript allow you to select one of two expressions based on the boolean result of the first expression. If the expression evaluates to TRUE the second expression will evaluate, if it’s FALSE the third expression will evaluate.


Let’s look at an example. Below we have an simple example of what a ticket might look like:



```json Airscript
{
    "id": "123",
    "description": "Hello World"
}

```

We can create an expression where we check whether the ticket matches the correct id. If it has the correct id, then it’ll return the description string, otherwise it’ll return the string "Not Found"



```javascript Airscript
IF(
  id = "123",
  description,
  "Not Found"
)
```

Because the second and third parameters are also expressions, we can nest these IF() expressions as well. We could check to make sure that the description also exists, and have a different response if there is no description present.



```javascript Airscript
IF(
  id = "123",
  IF(
    NOT(
      description = ""
    ),
    description,
    "No Description Found"
  ),
  "Not Found"
)
```

Complex Filtering and Querying
------------------------------


Airscript also provides a complex filtering and manipulation offering similar to SQL. This provides you the power of a query language, on top of the already powerful Airscript.


Let’s take an example where you have a list of objects that contain a question and selected answer. Here we see a list of questions, with only some of the answers filled in:



```json Airscript
listOfQuestions
  = [
    { "prompt": "What is your name?", "answer": "Nathan" },
    { "prompt": "Where do you work?", "answer": "Airkit" },
    { "prompt": "What's your favorite drink?", "answer": "" }
  ]
```

We can filter that list of questions down to only the questions that have answers, and then we can extract only the answers from those:



```javascript Airscript
FROM question IN listOfQuestions WHERE NOT(question.answer = "") SELECT question.answer
```

That would give us a filtered result of:



```javascript Airscript
["Nathan", "Airkit"]

```

Since, we’re still working with Airscript, we can also perform more advanced operations on the filtered data. We could join those answers into one string for use within a label. Our filter expression would change to this:



```javascript Airscript
JOIN(
  FROM
    question
  IN
    listOfQuestions
  WHERE
    NOT(
      question.answer = ""
    )
  SELECT
    "Question: {{question.prompt}} - Answer: {{question.answer}}",
  "
"
)
```

Which would give us the string:



```
Question: What is your name? - Answer: Nathan
Question: Where do you work? - Answer: Airkit
```