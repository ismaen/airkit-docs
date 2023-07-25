Application vs. Journey Assets
==============================


Airkit handles files and media in two ways on that is part of the application and shared across all users and the other is stored within a particular user's journey.


### App Assets


App Assets are files & media that are included in the application itself and can be referenced through the Studio when designing an experience. Examples Include:


1. Images in a web experience (PNG, JPG, etc.)
2. Documents to download (PDFs, ZIP etc.)
3. Or other media such as videos (MP4)


These assets need to be included in your [Media Library](https://support.airkit.com/docs/media-library) and are made available through special URLs that resolve securely to a user through your custom domain and quickly as through the Airkit CDN.  
  
![2021-03-11_12-30-52__1_.png](./assets_v1714/working-with-files-and-media-v1714-0).png)


 


### Journey Assets


Journey Assets are files that are associated with a specific user's journey within Airkit and can be stored within variables and used within data operations. Some common examples include:


1. [Photos captured](https://support.airkit.com/reference/media-upload-web-control) from a customers mobile device
2. [Files uploaded](https://support.airkit.com/reference/media-upload-web-control) from a customer
3. [Customer signatures](https://support.airkit.com/reference/signature-control) (PNG)
4. [Generated PDF files](https://support.airkit.com/docs/creating-a-pdf) (Form fills, merged PDFs or custom generated)


Because Journey Assets are stored in variables the scope of how long they are available is determined by whether the Journey is active or expired, please see [Journey State](https://support.airkit.com/docs/journeys) for more information.


 


Working with Assets in Variables
================================


The Asset data type of a variable allows you to work with files and media within a journey using [Airscript](https://support.airkit.com/docs/airscript-quick-start) and within [Data Flows](https://support.airkit.com/docs/data-flows).



<img src="./assets_v1714/working-with-files-and-media-v1714-1.gif" alt="organizing info" style="max-width: 350px; width:100%;"/>
### Real-World Use Cases


Some examples of when you might use a variable with the [Asset data type](https://support.airkit.com/reference/the-asset-data-type) to receive or handle a file


* The [Media Upload](https://support.airkit.com/reference/media-upload-web-control) web control to receive photos from a mobile device's camera or photo library
* The [Media Upload](https://support.airkit.com/reference/media-upload-web-control) web control to receive files from a mobile device or desktop
* The [Signature Pad](https://support.airkit.com/reference/signature-control) web control to capture a users hand-written e-signature
* Creating a new PDF from an HTML template with user specific values using the [HTML to PDF](https://support.airkit.com/reference/the-html-to-pdf-data-operation) Data Operation
* Filling the fields of a form-fillable PDF template with user specific values using [The Fill PDF Form Data Operation](https://support.airkit.com/reference/the-fill-pdf-form-data-operation)
* Merging the pages of multiple PDFs together using [The Merge PDF Data Operation](https://support.airkit.com/reference/the-merge-pdf-data-operation)
* Generating a flat file from journey or batch data using [The Create File Data Operation](https://support.airkit.com/reference/the-create-file-data-operation)
* Combining and compressing multiple files together with [The ZIP File Data Operation](https://support.airkit.com/reference/the-zip-file-data-operation)
* Sending files as attachments on emails with [The Send Email Data Operation](https://support.airkit.com/reference/the-send-email-data-operation)
* Sending files securely with [The SFTP Data Operation](https://support.airkit.com/reference/the-sftp-data-operation)
* Looking up file meta information with [The Fetch Asset Details Data Operation](https://support.airkit.com/reference/the-fetch-asset-details-data-operation)
* Deleting one or more Assets with [The Delete Assets Data Operation](https://support.airkit.com/reference/the-delete-assets-data-operation)
* Getting a temporary download URL to share with a user with [The Fetch Asset Details Data Operation](https://support.airkit.com/reference/the-fetch-asset-details-data-operation)


 


Embedding Assets within Your Application
========================================


Using [Media Library](https://support.airkit.com/docs/media-library) you can upload assets to be included and referenced in your application


<img src="./assets_v1714/working-with-files-and-media-v1714-2.gif" alt="organizing info" style="max-width: 350px; width:100%;"/>
 


Once a file has been uploaded into your Media Library you now have an Asset URI to use to reference the file while building your app.


 


Inserting Images using the [Image Web Control](https://support.airkit.com/reference/image-web-control)


<img src="./assets_v1714/working-with-files-and-media-v1714-3.gif" alt="organizing info" style="max-width: 350px; width:100%;"/>
#### 


### Why Does Airkit Use Special URLs for Assets?


You may notice that the way Airkit refers to files is not a typical URL and isn't able to be retrieved outside of the Airkit platform.  There are two primary reasons for using a specific URI



* **Security** - these Asset URIs can only be accessed in the context of an Airkit operation such as within a journey of a user and are dynamically exchanged for temporary URL
* **Version Control** - we want to make sure that files are tracked across versions of applications easily and caching issues do not arise


### What are the components of an Asset URI?

`asset://[Access Scope]:[Organization UUID]/[Application UUID]:[File UUID]:[Version Number]`
* **Access Scope**: Global or user specific
* **Organization UUID**: Your Organizations ID
* **Application UUID**: The specific branch of the application that is serving the asset.  This is used for version control so that asset links will still function for journeys that started on an older branch of your application
* **File UUID**: Uniquely represents the file within your application's Media Library
* **Version Number**: An auto-incrementing version number of an asset



 


Working with Assets in Data Operations
=====================================


### A quick walk through of some Data Operations that work with Assets



 


There are quite a few Data Operation that either produce files or consume files to perform their actions and all of these functions leverage the Asset variable type to provide or pass around references to the underlying files.  For example:


 


### Operations that Create or Consume Files


* [Create File](https://support.airkit.com/reference/the-create-file-data-operation) produces any file type and inserts content such as TXT, JSON, XML, CSV, TSV
* [Fill PDF Form](https://support.airkit.com/reference/the-fill-pdf-form-data-operation) takes a blank PDF template and merges values into form field to produce a filled PDF
* [HTML to PDF](https://support.airkit.com/reference/the-html-to-pdf-data-operation) creates a custom PDF using HTML for layout, styling and allowing full control over data and dynamic content including inserting images, CSS, footers/headers, page breaks and more
* [Merge PDF](https://support.airkit.com/reference/the-merge-pdf-data-operation) provides an operation to combine the pages of multiple PDF files into one PDF
* [Create ZIP File](https://support.airkit.com/reference/the-zip-file-data-operation) provides an operation to combine and compress multiple files into a single ZIP file


### Operations that Transmit Files Externally


* [Send Email](https://support.airkit.com/reference/the-send-email-data-operation) allows to attach one or more files to an outbound email originated from Airkit
* [SFTP](https://support.airkit.com/reference/the-sftp-data-operation) allows sending a file securely over FTP to remote server


### Operations that Support Asset Operations


* [Fetch Asset Details](https://support.airkit.com/reference/the-fetch-asset-details-data-operation) given an Asset URI looks up file details such as (name, type, size) and provides a temporary URL to download the underlying file
* [Delete Assets](https://support.airkit.com/reference/the-delete-assets-data-operation) removes the underlying file(s) from the server for an asset