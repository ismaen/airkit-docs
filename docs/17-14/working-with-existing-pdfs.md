A common workflow for our customers is to take an existing PDF and transform it into an Airkit App, allowing their users to complete the PDF digitally. The following video walks through the basics of taking a PDF form, uploading it, creating a Data Flow to populate the values of the form, and return a completed version of the PDF.


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F2gCopCxe6KQ%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D2gCopCxe6KQ&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F2gCopCxe6KQ%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=2gCopCxe6KQ",
  "title": "Filling a PDF",
  "favicon": "https://www.youtube.com/s/desktop/15c06292/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/2gCopCxe6KQ/hqdefault.jpg"
}
[/block]
Reading a PDF
-------------


Starting with the blank PDF, open it up in Adobe Acrobat. In the tools panel, find the **Prepare Form** toolbar. With this open, a list of all the available fields to complete will be present. Take note of the fields.


![PDF_-_PDF_Fields.png](./assets_v1714/working-with-existing-pdfs-v1714-0.png)


On the right-hand side, there is a list of fields that can be populated through the [Fill PDF Form Data Operation](https://support.airkit.com/reference/the-fill-pdf-form-data-operation). Airkit will be able to find all of these fields when processing the file.


To import the file go to [Media Library](https://support.airkit.com/docs/media-library) and upload the blank PDF template. Once the document has been uploaded, select the asset from the list. Copy the asset URI from the Inspector. The format is something like this:



```
asset://global:<<uuid>>
```

The data operation will require this URI.


Create the Data Flow
--------------------


Go to Connection Builder and create a new Data Flow. Set up the inputs to contain the fields to populate in the PDF. Set the first data operation to the [Fill PDF Form](https://support.airkit.com/reference/the-fill-pdf-form-data-operation) type. 

<img src="./assets_v1714/working-with-existing-pdfs-v1714-1.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

The **Filename** field is the name of the created PDF file once completed. The field is an expression editor so it can contain any Airscript. Check out [Working With Text in Airscript](https://support.airkit.com/docs/working-with-text-in-airscript) to see possibilities for the names.


The PDF File Asset Identifier is a link to the asset. Take the URI from above and use the [URI_TO_ASSET()](https://support.airkit.com/reference/uri_to_asset) function to create the asset:


```javascript Airscript
URI_TO_ASSET("asset://global:<<uuid>>")
```

Data to Fill contains an object where the key is the value of the label of the form field in the PDF and the value is the value to be inserted. For example:


```json Airscript
{   
  "YR Model": "2020 Model X",   
  "Print seller's name": sellerName,   
  "Printed Buyer's Name": buyerName  
}
```

"YR Model" is the labeled field in the PDF and "2020 Model X" is what will be filled in. The `sellerName` and `buyerName` text variables were inputs to the Data Flow.


Asset settings pertain to the visibility and length of life of the asset. See the documentation on [Fill PDF Form](https://support.airkit.com/reference/the-fill-pdf-form-data-operation) for more details.


Understanding the Output
------------------------
Running the connection step produces the following output:


```json Airscript
{  
  "id": "886aad07-8027-4381-95cc-a59519c857f3",  
  "assetKey": "21ebf873-38e0-4cbb-af76-912f67cf9036",  
  "organizationId": "395f62e5-6437-4ef0-9505-8a21a4c89e0b",  
  "displayName": "bill_of_sale.pdf",  
  "description": null,  
  "type": "application/pdf",  
  "size": 51997,  
  "version": 0,  
  "expiration": 604800000,  
  "visibility": "PRIVATE",  
  "state": "ACTIVE",  
  "scope": "APP",  
  "region": "us-west-2",  
  "createdTime": "2021-03-31T12:14:12.587Z",  
  "modifiedTime": "2021-03-31T12:14:14.414Z",  
  "deletedTime": null,  
  "validationErrors": null,  
  "extraInfo": null,  
  "downloadUrl": "https://s3.us-west-2.amazonaws.com/ruist-assets-private-prod-us-west-2/395f62e5-6437-4ef0-9505-8a21a4c89e0b/21ebf873-38e0-4cbb-af76-912f67cf9036/886aad07-8027-4381-95cc-a59519c857f3/0?response-content-disposition=attachment%3Bfilename%3Dbill_of_sale.pdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20210331T121415Z&X-Amz-SignedHeaders=host&X-Amz-Expires=604800&X-Amz-Credential=AKIARVCWII5ZB4BK2J6K%2F20210331%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Signature=6d790b2c95fb283e3ed85a8a03cc9bfe1bd39d0cbff6c5cefa1a59cf03301da3",  
  "thumbnailUrl": null  
}
```

The `downloadUrl` field in the output is a link to the complete PDF. This link can be returned from the data flow, stored in [AirData](https://support.airkit.com/docs/working-with-data), or sent to the user via email.