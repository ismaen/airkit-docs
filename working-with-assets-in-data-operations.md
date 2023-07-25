Assets are Airkit's representation of files. Assets can be created, manipulated, and transmitted via Data Operations in [Connection Builder](https://support.airkit.com/docs/connection-builder). Assets are great to remit out of a data flow to a system of records.  

## Working with Text + JSON files

Text files are the most basic of files. They are free form and made up of nothing but characters. There are no requirements. Creating a text file in Airkit is done with the [Create File](https://support.airkit.com/reference/the-create-file-data-operation) data operation. Let's create a simple record of someone expressing interest in a property.

Go to Connection Builder and create a new Data Flow. Set this Data Flow to have two inputs, one of type House (or type Any if you do not have a House AirData App Object) name **house** and one of type Any named **person**. Paste some sample data into **house**:

```json JSON
{  
  "__id": "b03fb0dc-c6b4-4b87-ae0a-23cf0fbb2db9",  
  "image": {  
    "id": "946c295f-684f-41be-a2ed-2f90df70c35d",  
    "assetKey": "ab69d4c4-5ff9-42b5-b8c7-7e479cc0bbba",  
    "organizationId": "395f62e5-6437-4ef0-9505-8a21a4c89e0b",  
    "visibility": "GLOBAL",  
    "version": 0  
  },  
  "baths": 2,  
  "asking": {  
    "amount": 30000000,  
    "precision": 2,  
    "code": "USD"  
  },  
  "square_feet": 3252,  
  "beds": 3,  
  "date_available": {  
    "year": 2021,  
    "month": 4,  
    "day": 7  
  },  
  "title": "Little Prairie",  
  "contact_email": "bob@example.com"  
}
```



and paste some sample data into **person**:

```json JSON
{  
  "name": "Jane Smith",  
  "email": "jane@example.com"  
}
```



Select _[Create File](https://support.airkit.com/reference/the-create-file-data-operation)_ data operation for the first data operation. Let's use the property title and person name to create a unique filename for this file. In the _Filename_ field, enter: 

```
"House-{{house.title}}-by-{{person.name}}.txt"
```



The example above creates a file named "House-Little Prairie-by-Jane Smith.txt." This ensures that each file will be labeled with the property and the interested party's name.

The _Content_ is where to place the file text. Put the following into the box:

```text Text
"Property: {{house.title}}  
Asking: {{FORMAT_CURRENCY(house.asking)}}  
Date Requested: {{FORMAT_DATETIME(NOW(), "MM/DD/YYYY")}}  
  
Interested Party: {{person.name}}  
Interested Party Email: {{person.email}}"
```



This will output a file named "House-Little Prairie-by-Jane Smith.txt."

```
Property: Little Prairie  
Asking: $300,000.00  
Date Requested: 04/15/2021  
  
Interested Party: Jane Smith  
Interested Party Email: jane@example.com
```



### Working with JSON

In the text example above, the documentation format is very easily readable by humans, but many APIs prefer a JSON or (JavaScript Object Notation) formatted document. Converting the previous example to JSON, create a new data operation and change the file name to:

```Text JSON
"House-{{house.title}}-by-{{person.name}}.json"
```



Replace the Content box with:

```json JSON
{  
  "property": "{{house.title}}",  
  "asking": "{{FORMAT_CURRENCY(house.asking)}}",  
  "date requested": "{{FORMAT_DATETIME(NOW(), "MM/DD/YYYY")}}",  
  "interested party": "{{person.name}}",  
  "interested party email": "{{person.email}}"  
}
```



This will return a file with the following contents:

```json JSON
{  
  "property": "Little Prairie",  
  "asking": "$300,000.00",  
  "date requested": "04/15/2021",  
  "interested party": "Jane Smith",  
  "interested party email": "jane@example.com"  
}
```



This is valid JSON but did require many escape characters for the quotes. It also loses some of the data stored in the Person and House objects.  It is possible to convert an entire object to JSON using [TO_JSON()](https://support.airkit.com/reference/to_json). Using this function, it is possible to quickly convert the entire house and person objects over to JSON for our file. Replace the Content with:

```json JSON
{  
  "house": {{TO_JSON(house)}},  
  "person": {{TO_JSON(person)}}  
}
```



The resulting file should look like this:

```json JSON
{  
  "house": {  
     "__id": "b03fb0dc-c6b4-4b87-ae0a-23cf0fbb2db9",  
     "asking": {  
        "amount": 30000000,  
        "code": "USD",  
        "precision": 2  
     },  
     "baths": 2,  
     "beds": 3,  
     "contact_email": "bob@example.com",  
     "date_available": {  
       "day": 7,  
       "month": 4,  
       "year": 2021  
     },  
     "image": {  
       "assetKey": "ab69d4c4-5ff9-42b5-b8c7-7e479cc0bbba",  
       "id": "946c295f-684f-41be-a2ed-2f90df70c35d",  
       "organizationId": "395f62e5-6437-4ef0-9505-8a21a4c89e0b",  
       "version": 0,  
       "visibility": "GLOBAL"  
     },  
     "square_feet": 3252,  
     "title": "Little Prairie"  
  },  
  "person": {  
     "email": "jane@example.com",  
     "name": "Jane Smith"  
  }  
}
```



Notice how this version even has the ID for the image and other properties. Depending on the use case, it might be ideal for sending the entire object or just part of the object. For more information on object encoding, read [Encoding in Airscript (URLs & Base64)](https://support.airkit.com/docs/encoding-in-airscript-urls-and-base64).

## Creating PDFs

Another output format is PDF. PDFs allow the creator to determine the visual appearance of the expected output and have it be consistent across many different devices. In Airkit, PDFs are created using the [HTML to PDF](https://support.airkit.com/reference/the-html-to-pdf-data-operation) data operation.

Create a new Data Flow with the same inputs as the flow above. Let's create a PDF with information on the house in a table format, in a letter format to the person interested.

Select HTML to PDF for the data operation step type. Enter the following HTML into the HTML box:

```html
<h1>Property Interest Letter</h1>  
<p>Dear {{person.name}},</p>  
  
<p>Thank you for expressing interest in our property, {{house.title}}. Here are  
the details on the property you expresssed interest in:</p>  
  
<table>  
  <tr>  
     <th>Title</th>  
     <td>{{house.title}}</td>  
  </tr>  
  <tr>  
     <th>Beds</th>  
     <td>{{FORMAT_NUMBER(house.beds, "#")}}</td>  
  </tr>  
  <tr>  
     <th>Baths</th>  
     <td>{{FORMAT_NUMBER(house.baths, "#")}}</td>  
  </tr>  
  <tr>  
     <th>Asking Price</th>  
     <td>{{FORMAT_CURRENCY(house.asking)}}</td>  
  </tr>  
</table>  
  
<p>Please feel free to reach out to {{house.contact_email}} with any additional  
questions!</p>
```



The resulting file should look like this:

<img src="./assets_v1714/working-with-assets-in-data-operations-v1714-0.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

While this is a very bland and simple example, it is possible to use many more features of inline HTML to include links, lists, and additional formatting.

## Merging Multiple Files into a Zip

In addition to creating files, it is possible to combine files into a compressed zip document using the [Zip File Data Operation](https://support.airkit.com/reference/the-zip-file-data-operation). This operation takes an array of assets, compresses it into a zip file, and returns a newly created asset for the combined, compressed files. Zip files are useful for grouping many items together for archiving or sending via a network as they take up less space than non-compressed files.

Let's combine the text file and the pdf for the records. Create a new Data Flow that creates both the text file in the default **file** output and a PDF file in the default **htmlToPdf** output. Ensure both data operations have run so the assets point to real files. Add a new Data Operation of type _Zip File_. The _Files to zip_ field takes an array of assets set it to:

```
[ file, htmlToPdf ]
```



The _Zip Filename_ refers to the name of the created file. Name it as we have above:

```
"House-{{house.title}}-by-{{person.name}}.zip"
```



Hit play on the data operation. The resulting zip file will have a download link. Copy and paste that into a new browser window to download the file. It should contain the text and the PDF files created from the previous examples.

## Encrypting files with PGP

Some files have sensitive data. Airkit takes security seriously. It is possible to PGP (Pretty Good Privacy) encrypt your files for sending. This section will assume knowledge of PGP and access to a public PGP to be used in the encryption.

To encrypt the zip file created in the example above, set the _Output Filename_ to:

```
"House-{{house.title}}-by-{{person.name}}.pgp"
```



Set the File to encrypt to the **zipFile** created above. For the PGP Key, use the public PGP key for the encryption. It usually starts with "-----BEGIN PGP PUBLIC KEY BLOCK-----." The data operation should look like this:

<img src="./assets_v1714/working-with-assets-in-data-operations-v1714-1.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

Running the data operation will create an encrypted file asset. Download the PGP encrypted document and decode using the matching private key.

## Other Usages

In addition to the examples discussed above, Assets are used throughout Airkit Applications. Assets refer to data that is not rendered in a text format on the screen. This includes images, videos, calendar invites, and other coded data. While the examples above show some basics of working with Assets, the possibilities are endless with the flexibility of the Airkit Platform. Applications have been written to integrate with proprietary data systems. 

[Working with Files & Media](https://support.airkit.com/docs/working-with-files-and-media) talks about working with media assets like images and other files. [Integrating to External Calendar Systems](https://support.airkit.com/docs/integrating-to-external-calendar-systems) shows how to integrate external calendar ICS assets. [Working with Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript) is a good reference for understanding how to work with data to create custom formatted text.