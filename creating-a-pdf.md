Introduction
------------


PDFs generated in Airkit can be transferred to either the user or an external system. This allows you to use these PDF capabilities everywhere, from within your app to remitting to external sources.


Let's dive into how you create and fill PDFs with Airkit.


Adding a Data Flow
-----------------------


Once you’ve opened your application in Airkit Studio, head on over to the **Connection Builder** to get started.

<img src="./assets_v1714/creating-a-pdf-v1714-0.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Data Flows allow you to perform a multitude of operations over data. Inside Connection Builder, click on the ‘+' next to Data Flows to create a blank Data flow, and name it whatever you’d like. Below **Start**, click the '**+**' button, to select a Data Operation. We'll discuss two: **HTML to PDF** and **Fill PDF Form**.


HTML to PDF
-----------


This Data Operation is specially useful when needing to collect and process information that is generated along your application journey and dump it into a downloadable file.


This Data Operation has two mandatory settings and a couple more that can be left blank for the purpose of learning how to use it (but which may come in handy in a real world usage).


1. **HTML**: is the HTML code you’ll want converted into a PDF file.
2. **PDF Filename**: is the name the data op will use to name the resulting PDF file.


When running the Data Operation, the HTML to PDF will build a PDF asset from the HTML entered and the object returned will contain the download url of the asset. [See source code examples.](https://support.airkit.com/docs/example-html-code-to-create-a-pdf)

Fill PDF Form
-------------

Sometimes you’ll want to fill in information into a PDF fillable form instead of creating the PDF file from scratch.

This is what the Fill PDF Form Data Operation is for: you can collect and process information that is generated along your application journey and then insert it into pre-defined fields in a PDF form.

This Data Operation has three mandatory settings. There are a couple more that can be left blank for the purpose of learning how to use it (but which may come in handy in a real world usage).

1. **Filename**: is the name the data operation will use to name the resulting PDF file.
2. **PDF File Asset Identifier**: is the asset URI of your PDF form. To obtain it, you will need to have your PDF form uploaded into your app’s Media Library, select it from the list of files and copy the URI shown on the right hand properties pane.
3. **Data to Fill**: is the payload that you will insert into the PDF form.
    `{"key_name":"payload_value"}`
Where **key_name** is the name of the PDF form text field you’d like to insert **payload_value** into.

When running the Data Operation, the payload will be inserted into the PDF form and the object returned will contain the download url of the asset (along other properties).