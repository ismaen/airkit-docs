Data encryption enhances the security of an application by securing content that may be considered sensitive data. For example, when building out an application that captures a social security number, this data can be considered sensitive and would need to be encrypted. Whether that data is a field within an app object or a variable created in an activity (web flow, web page, chat bot, voice bot), any of that data can be encrypted in the studio.  



Encryption Keys
---------------


In order to encrypt/decrypt data, this requires an encryption key. There are two options when using encryption keys within Airkit, developers can either use the default keys that get created or bring your own encryption key.  


### Default Keys


Every Airkit Organization get encryption keys automatically provisioned for each datastore (Development, QA, and Production). These keys are created using [AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) and are provisioned with the default configuration.

<img src="./assets_v1714/encrypting-data-v1714-0.png" alt="organizing info" style="max-width: 500px; width:100%"/>

### Bring your own Keys


If the default key configuration does not meet security requirements, a [custom AWS KMS Key](https://aws.amazon.com/kms/features/#Custom_Key_Store) can be created outside of Airkit and be associated to a datastore.

To create a custom encryption key, go to [console.airkit.com](https://console.airkit.com) > Settings > Encryption Keys and select **Create new**. 

<img src="./assets_v1714/encrypting-data-v1714-1.png" alt="organizing info" style="max-width: 150px; width:100%"/>
<img src="./assets_v1714/encrypting-data-v1714-2.png" alt="organizing info" style="max-width: 300px; width:100%"/>

Enter a name for the custom key and pass the Reference Key. The reference key is the Amazon Resource Name (ARN) of the KMS Key. To find the ARN see [here](https://docs.aws.amazon.com/kms/latest/developerguide/find-cmk-id-arn.html). 


Encrypting Variables
--------------------


Variables created in the studio can be encrypted to secure sensitive data. After encrypting a variable, the variable can still be read and set like normal across an application and within app preview - the only difference is that when it is stored in in Airkit's databases, the variables will be encrypted. 


To encrypt a variable, right click on the variable and select **Encrypt**. 


<img src="./assets_v1714/encrypting-data-v1714-3.png" alt="organizing info" style="max-width: 300px; width:100%"/>

Encrypting Fields in AirData
----------------------------


Fields in AirData can also be encrypted to secure sensitive content using the encryption key associated with the datastore. To associate an encryption key to a datastore, go to [console.airkit.com](https://console.airkit.com) > **Datastores** and select a datastore.  Then select the Encryption tab and an encryption key from the dropdown list.  
![mceclip4.png](./assets_v1714/encrypting-data-v1714-4.png)  
To encrypt fields in an AirData App Object, go to Data Builder and select one of the fields of a created App Object. Then in the Inspector check the Encrypt flag to encrypt that field.   
![mceclip5.gif](./assets_v1714/encrypting-data-v1714-5.gif)  
This will encrypt that field when the data is stored.


**Note:** There are limitations to data that is encrypted which include not being able to search or filter on that field.