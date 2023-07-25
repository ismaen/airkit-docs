# What is a Data Flow?


Data Flows are custom connections. Conceptually, Data Flows work like functions: they take in input, process it, and return the resulting output (if applicable). Once a Data Flow has been built, it can be initiated as an [Action](https://support.airkit.com/docs/action-builder) within your application, or as a [Periodic Task](https://support.airkit.com/docs/setting-up-periodic-tasks).


Data Flows are made up of component parts called [Data Operations](https://support.airkit.com/reference/data-operation-overview), which define how input is processed. Processing input might entail anything from [making HTTP requests](https://support.airkit.com/reference/http-request-data-operation) to [sending emails](https://support.airkit.com/reference/the-send-email-data-operation) to [running another Data Flow](https://support.airkit.com/reference/the-run-data-flow-data-operation). 


# The layout of a Data Flow


Data Flows are created in Connection Builder. Data Flows are one type of connection. Data Flows are initiated by some other part of your application. With a Data Flow selected, the layout of Connection Builder appears as follows:


![Airhome-DataFlows-FullScreen.png](./assets_v1714/data-flows-v1714-0.png)


The Tree shows the Data Flows available for selection, the Stage shows the Data Operation Steps of the selected Data Flow, and the Inspector shows the available parameters at the different steps throughout the Data Flow.


A single Data Flow might consist of any number of interconnected Data Operations, though these Data Operations do not appear nested underneath them in the Tree; building Data Flows out of Data Operations is done in the Stage. When a Data Flow is called, the operation steps are executed sequentially starting at the top and working down the Stage. The outputs from each Data Operation Step are available to use as input in the following steps. 


To add a new Data Operation to an existing Data Flow, click on the '+' icon where you want to insert it. For instance, to add a Data Operation between the [AirData Request Data Operation](https://support.airkit.com/reference/airdata-request-data-operation) and the [Transform AirData Request](https://support.airkit.com/reference/the-transform-data-operation) in the following example, click on the '+' icon between them:

<img src="./assets_v1714/data-flows-v1714-1.png" alt="organizing info" style="max-width: 300px; width:100%">

# Start and End of Data Flows


There are two special boxes in the Stage of the Data Flow. The Start block represents variables that are to be sent into the Data Flow. In the Start box, provide demo data that will be used throughout the testing of the Data Flow in Connection Builder. This demo data does NOT represent default values, and it will have no bearing on the the Data Flow when it is used as part of an application. It will only be used to when a dummy value for that variable is required in order to test Data Operations within the Web Flow within the Stage.


Because the start parameters are user entered, be careful to make sure the properties of the start parameters match the format of the values the Data Flow will receive. You will receive a warning if the data is not in the format expected. Start parameters are available in any of the data operations throughout the flow.


The End block represents the value to be returned in the output block of the Data Flow. In Web Builder, this is the output you specify in the [Run Data Flow](https://support.airkit.com/reference/the-run-data-flow-action) Action.


# Data Operation Frame


Other than the start and end Frame of the Data Flow, each block in the stage represents an individual Data Operation. Each contents of each Data Operation are different, reflecting the unique functionality of each Data Operation. (For a more complete look into the different types of Data Operation, see [the reference documentation](ref:data-operation-overview).) A sample Data Operation looks as follows:


![Airhome-DataFlows-DataOp.png](./assets_v1714/data-flows-v1714-2.png)


On the left of the frame is the frame number. Frames are numbered sequentially and used to match up the variables on the right in the inspector. This Data Operation is of type **Transform**, and that is denoted at the top of the frame. The Top part of the frame is about the action to be performed. In this case, there is a **Transform Expression** that contains Airscript that is run when the operation is called. The Output Format specifies the variable options for return. Many Data Operations will have different configuration options. 


The bottom of the Data Frame deals with the **Run Results** of the Data Operation. Most data Operations return a single item, with a default name. In the case above, the Transform returns a default ```transform``` variable. It is possible to rename the output by double-clicking the value in the Inspector under the frame number. Some operations, like the [HTTP Request Data Operation](ref:http-request-data-operation), will have multiple different outputs. Each output will have a tab in the **Run Results** section.