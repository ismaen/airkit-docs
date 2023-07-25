Assets that are uploaded through the [File Upload](ref:file-upload-web-control) control can be then be uploaded to a remote server or other file repositories through the [HTTP Request](ref:http-request-data-operation) data operation. 

When using the HTTP request data operation to upload files, there are a few things you can do depending on the system's requirements.

# Download Encoded Asset

If the system requires to pass a BASE64 encoded asset, use the  [Download Encoded Asset](ref:download-encoded-asset-data-operation) data operation. 

![encoded_asset](./assets_v1714/uploading-assets-to-a-remote-server-v1714-0.png)

# Multipart/form-data

The [HTTP Request](ref:http-request-data-operation) data operation supports the `multipart/form-data` content type, which when you make the request to the system with the asset, will send the binary data for the asset instead of the URL.


<img src="./assets_v1714/uploading-assets-to-a-remote-server-v1714-1.png" alt="organizing info" style="max-width: 550px; width:100%;"/>

# Encoding
Furthermore, if the file or asset needs to be encoded, there are some Airscript functions that may be applicable, depending on the system.

* [BASE](ref:base) 
* [BASE64_DECODE](ref:base64_decode) 
* [BASE64_ENCODE](ref:base64_encode) 
* [HMAC_MD5](ref:hmac_md5) 
* [HMAC_MD5](ref:hmac_md5) 
* [HMAC_SHA1](ref:hmac_sha1) 
* [HMAC_SHA256](ref:hmac_sha256) 
* [MD5](ref:md5) 
* [SHA1](ref:sha1) 
* [SHA256](ref:sha256) 
* [URL_ENCODE](ref:url_encode) 
* [URL_DECODE](ref:url_decode)