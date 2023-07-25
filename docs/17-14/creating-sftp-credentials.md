[The SFTP Data Operation](https://support.airkit.com/reference/the-sftp-data-operation) requires the use of SFTP credentials. Airkit supports connecting to an SFTP server via either Username / Password or Authentication Key. This article will walk through creating an SFTP credentail to use with the SFTP Data Operation.


SFTP credentials are created in [Console.](https://support.airkit.com/docs/console) When inside the studio, click the Airkit Logo at the top of the builder bar to return to the console. Select integrations from the options on the left. With *Connected Accounts* selected, click the *New* button in the top right corner. Select SFTP From the integration.


![SFTP-Creds-Console.png](./assets_v1714/creating-sftp-credentials-v1714-0.png)




[block:callout]
{
  "type": "info",
  "body": "If you don't have SFTP as an option for the integration dropdown, please contact [Airkit Support](mailto:support@airkit.com)."
}
[/block]
The Name property applies to either Authentication Model. Enter a name that will allow you to identify the credentials.


Using Username / Password
-------------------------


To use the standard username and password method. Fill out the username and password and click create. Understand that while this method is available, this method is not as secure as the private key method. 


![SFTP-Creds-UsernamePassword.png](./assets_v1714/creating-sftp-credentials-v1714-1.png)


Using Private Key
-----------------


Using a private key will not use a password. To configure the Private key, the public key must be part of the **authorized_keys** on the server. In the SFTP credentials box enter the username and the private key. Click create.


![SFTP-Creds-UsernameKey.png](./assets_v1714/creating-sftp-credentials-v1714-2.png)



[block:callout]
{
  "type": "info",
  "body": "Airkit supports private keys in OpenSSH format."
}
[/block]
Configuring an App To Use Credentials
-------------------------------------


Once the credentials have been configured, the credentials need to be added to an app through [Configuration Builder](https://support.airkit.com/docs/configuration-builder). Open the app and select configuration builder. Scroll down to the Integrations section. Select *New > Adapters > SFTP*. 


![SFTP-Integration-ConfigurationBuilder.png](./assets_v1714/creating-sftp-credentials-v1714-3.png)


Next, select the created credential in the dropdown under Connected Account.


To use this in a [Data Flow](https://support.airkit.com/docs/data-flows) go to [Connection Builder](https://support.airkit.com/docs/connection-builder). Select the data flow and add a data operation of type SFTP. Select the integration you created from the dropdown option for the data source. Fill out the rest of the options from [the SFTP Data Operation](https://support.airkit.com/reference/the-sftp-data-operation). 


Further Reading
---------------


* [The SFTP Data Operation](https://support.airkit.com/reference/the-sftp-data-operation) - for all the properties of the data operation.
* [Working with Assets in Data Operations](https://support.airkit.com/docs/working-with-assets-in-data-operations) - for a bigger explanation of how to work assets in Data Flows.