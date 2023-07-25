When working with Airscript, it's often advantageous to test an Airscript expression before implementing it. This is especially true if the Airscript expressions are long and complicated, or the output of the expression won't appear in the [Stage](https://support.airkit.com/docs/studio) of the [Web Builder](https://support.airkit.com/docs/web-builder) (which occurs if the Airscript expression is part of a conditional or if the Airscript expression requires user input in order to resolve). In this article, we'll walk through a way to test Airscript expressions and immediately see if they return the expected results.


Testing Airscript expressions requires accessing to the [Airkit Studio](https://support.airkit.com/docs/studio). It doesn't matter what application you have open within it: you can set up your tests directly inside of whatever large application you're working in, or you can create a new app entirely for testing purposes.


This article covers *how* to test, not *what* to test. For a deeper discussion into the syntax of Airscript expressions, check out the [Airscript Quickstart](https://support.airkit.com/docs/airscript-quick-start).



### Setting up a designated Data Flow to test Airscript Expressions


1. Toggle over to the [Connection Builder](https://support.airkit.com/docs/connection-builder) by clicking on the associated button within the [Builder Bar](https://support.airkit.com/docs/builder-bar):

<img src="./assets_v1714/testing-airscript-expressions-v1714-0.png" alt="connection builder" style="max-width: 350px; width:100%"/>


2. Create a new [Data Flow](https://support.airkit.com/docs/data-flows) by clicking the '+' icon to the right of **Data Flows** in the Tree:

<img src="./assets_v1714/testing-airscript-expressions-v1714-1.png" alt="new data flow" style="max-width: 350px; width:100%"/>


3. Click **Create Blank** from the pop-up window that appears:

<img src="./assets_v1714/testing-airscript-expressions-v1714-2.png" alt="create blank" style="max-width: 850px; width:100%"/>


This will create a new, blank Data Flow.


4. Double-click on the new Data Flow within the Tree and name this new Data Flow "Airscript Testing":

<img src="./assets_v1714/testing-airscript-expressions-v1714-3.png" alt="create blank" style="max-width: 650px; width:100%"/>


5. Click on the '+' button between the **Start** and **End** boxes in the Stage:


![2021-11-23_11-32-29.png](./assets_v1714/testing-airscript-expressions-v1714-4.png)


6. Select **Transform** from the pop-up window that appears:


![2021-11-23_11-34-17.png](./assets_v1714/testing-airscript-expressions-v1714-5.png)


7. A [Transform Data Operation](https://support.airkit.com/reference/the-transform-data-operation) will appear between the **Start** and **End** boxes in the Stage. Enter the Airscript expression you mean to test under **Transform Expression**. For example, to examine what is returned by the [NOW](https://support.airkit.com/reference/now) function, it should look like this:

<img src="./assets_v1714/testing-airscript-expressions-v1714-6.png" alt="create blank" style="max-width: 650px; width:100%"/>



8. Press the **Run** button Under the **Run Results** section of the Transform Data Operation. This will run the Airscript expression entered above and return the output of the expression:


<img src="./assets_v1714/testing-airscript-expressions-v1714-7.gif" alt="create blank" style="max-width: 450px; width:100%"/>



(Note that the output of the [NOW](https://support.airkit.com/reference/now) function is a [DateTime](https://support.airkit.com/reference/datetime).)


Any number of changes can be made to the Airkit expression under **Transform Expression**, and the Transform Data Operation can be run each time a change is made, to confirm that the changes to the Airscript expression resulted in the desired changes in behavior. All future testing of Airscript expressions can be done in this Transform Data Operation, within the Data Flow designated "Airscript Testing". 


### Feeding input into an Airscript Expression


The [NOW](https://support.airkit.com/reference/now) function does not require any input in order to run successfully, but many Airscript expressions do. There are two main ways to feed input into an Airscript expression: hardcoding, or calling on variables defined at the **Start** of the Data Flow. Any combination of these two options can be used if an expression requires multiple input parameters.


#### Hardcoding


Airscript expressions can be tested by directly hardcoding the desired input into the expression. For instance, to use the [ISODD](https://support.airkit.com/reference/isodd) function to test if the number 2 is odd, you could directly enter the expression:



```javascript Airscript
ISODD(2)
```

Inside of the Transform Data Operation, this would appear as follows. Note that at the time this screenshot was taken, the expression was run, returning the output **FALSE**, as 2 is not an odd number.


![2021-11-23_13-13-39.png](https://a01-support.airkit.com/testing-airscript-expressions/2021-11-23_13-13-39.png)


 


Most Airscript expressions expect input of a certain [data type](https://support.airkit.com/reference/data-types-overview). All data types can be hardcoded, though some require particular signifiers to be Airscript-parsable. [Text](https://support.airkit.com/reference/the-text-variable-data-type), for instance, must be designated by surrounding the relevant string with quotation marks. For a deeper dive into the different data types Airscript recognizes, check out the [Data Types Overview](https://support.airkit.com/reference/data-types-overview).


#### Calling on variables


The Transform Data Operation has access to all variables defined as part of the Airscript Testing Data Flow. When a Data Flow is first created, this section is blank, but new inputs can be defined in the Inspector, under the **Start** section. A Data Flow can keep track of arbitrarily many variables. 


Click on the '+' icon to the right of **Inputs** to define a new variable:


![2021-11-23_13-15-08.png](https://a01-support.airkit.com/testing-airscript-expressions/2021-11-23_13-15-08.png)


Upon clicking on the '+', a pop-up window will appear. Select the [Data Type](https://support.airkit.com/reference/data-types-overview) of the variable you mean to use as input when testing your Airscript expression: 


<img src="https://a01-support.airkit.com/testing-airscript-expressions/2021-11-23_13-16-38.png" alt="create blank" style="max-width: 250px; width:100%"/>


After defining selecting a variable type, give that variable a name by entering it in the text box that appears to the immediate right of the data type icon. This name will define how the variable will be designated when called upon by a downstream Airscript expression.


The following example shows two variables, a DateTime called ```example_datetime``` and a Number called ```example_number```:


![2021-11-23_13-19-01.png](https://a01-support.airkit.com/testing-airscript-expressions/2021-11-23_13-19-01.png)


Upon their creation, variables defined in a Data Flow will be automatically populated with dummy data of the correct type. This dummy data can be both examined and edited in the **Start** box. Select which variable you want to examine at any given time by clicking on the variable names at the top of the **Start** box:


![2021-11-24_11-58-45.png](https://a01-support.airkit.com/testing-airscript-expressions/2021-11-24_11-58-45.png)


When the Transform Data Operation is run, it will reference the dummy values defined in the **Start** box whenever the variable is called upon.


These variables can now be called on within the Airscript expression in the downstream Transform Data Operation.


As an example, consider testing the function [ADD_TO_DATETIME](https://support.airkit.com/reference/add_to_datetime). This function requires a DateTime, a Number, and a string. The following expression uses the value of ```example_datetime``` as the DateTime, the value of ```example_number``` as the Number, and hardcodes the string "hour" as the value for the string. (Remember: any combination of these hardcoded and variable parameters can be used if an expression requires multiple input parameters.)



```javascript Airscript
ADD_TO_DATETIME(example_datetime, example_number, "hour")
```

Running this within the Transform Data Operation yields the following results:


![2021-11-24_11-57-19.png](./assets_v1714/testing-airscript-expressions-v1714-8.png)


Note that this returns a DateTime that looks nearly identical to the value of ```example_datetime``` shown above, but that the hour attribute has increased by 1 – that is, it increased by the value of ```example_number```.


Changing the dummy values defined in the **Start** box and then running the Transform Data Operation again will return results that reflect the changes made. This makes it easy to test how Airscript expressions behave when given different values as input.


For more on defining variables in Data Flows, check out [this article](https://support.airkit.com/docs/data-flows) on the structure of Data Flows.


### Applying your tests


Airscript expressions can be used in a wide variety of places within your Airkit Application. Whenever a text box contains the ![2021-11-23_13-24-47.png](./assets_v1714/testing-airscript-expressions-v1714-9.png) icon on the bottom right, that means that entered values will be parsed as Airscript by default.


In the case of [Labels](https://support.airkit.com/reference/label-web-control), Airscript expressions can also be inserted into a string by applying double curly brackets around them. For instance, given some ```example_expression``` that returns [Text](https://support.airkit.com/reference/the-text-variable-data-type), the output of the expression can be displayed seamlessly within the existing string:



```javascript Airscript
"The output of the Airscript expression is {{example_expression}}"
```

If, say, the value of ```example_expression``` is "Hello, World", then this Label will display the text: "The output of the Airscript expression is Hello, World".