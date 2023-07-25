Overview
--------


SSO is an authentication process that allows users to log in to multiple independent applications with a single set of credentials. With SSO, users can access a suite of applications via one single login, irrespective of the platform, technology, or domain used. This reduces security risks surrounding user data, improves the user experience, and streamline IT management and login processes. 


SAML SSO and how does it works
------------------------------


One of its most used protocols, SAML, allows identity providers (IdPs) to store user identity data and authenticate those users to other applications using public-key cryptography.


An i(IdP) can be a cloud-based identity service like Okta, OneLogin or an internal enterprise resource like Azure AD. Meanwhile, a service provider (SP) is the application a user wants to access, in this case Airkit. As long as the IdP can authenticate the user, the SP will let them in.


When a user logs into an application using SAML, the IdP will send a SAML assertion to their browser that is then sent to the SP. The SAML assertion is an XML file with three statement types: authentication, attribution and authorization. 


How to setup SAML SSO in Airkit
-------------------------------


**Important**: Airkit currently supports SP initiated flow only. This means that users will have to access their application directly through Airkit’s Studio URL, which then re-directs them to the corresponding IdP for authentication.


In order to configure SAML SSO access to Airkit the SAML Assertion Metadata must be generated from the IdP of choice. It will be used to share configuration cretendials between the IdP and the SP. The IdP metadata usually contains the IdP certificate, the entity ID, the redirect URL, and the logout URL. 


This XML file needs to be uploaded in the app, and determines which IdP should be receiving the SAML request. This is done in the [Console](https://support.airkit.com/docs/console). When inside the [studio](https://support.airkit.com/docs/studio), click the Airkit Logo at the top of the builder bar to return to the Console. Select **Settings** from the options on the left. Then, from the submenu, select **SAML** and click the New button in the top right corner. Click on the dialog box located on the right side of the screen and manually upload the XML file, or simply drag and drop it to begin the upload instantly. Finally, press Create in order to generate the SAML configuration. 


*![L5F3t87hYX.png](./assets_v1714/configuring-sso-access-for-an-organization-v1714-0.png)*


**Note**: Refer to the next step in order to extract ACS URL & Entity ID. Do not use the ones that are displayed right after uploading the SAML metadata.


Afterwards, go back to **Settings**, then select **Organization**, and from the **Authentication** dropdown list located on the center of the screen choose the XML file that was uploaded in the previous step. Doing so will display the following credentials which should be used to finish the SAML integration on the IdP end  



* **SAML Login URL:** link that users will utilize to access their application. Should redirect to IdP for authentication.
* **ACS URL:** directs your IdP where to send its SAML Response after authenticating a user
* **Entity ID:** dictates the entity or audience the SAML Assertion is intended for. Usually in the form of a URL that contains the Service Provider's name within, and is often simply the same URL as the ACS


The EntityID and ACS URL, in particular, must be used to whitelist Airkit in the IdP configuration. This process may vary depending on which IdP is being used.


![chrome_fqjQGCWzEY.png](./assets_v1714/configuring-sso-access-for-an-organization-v1714-1.png)


 


After setting up the credentials on both ends, users may access Airkit's Studio using the above mentioned SAML Login URL.


Support
-------


If you need assistance with setting this up, feel free to file a support ticket with Airkit Support.