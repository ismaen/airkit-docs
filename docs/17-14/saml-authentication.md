This article will cover how to configure an Airkit application to use SAML Authentication. In order to set up this authentication, there are few configurations needed at the organization level.

Download the SAML Metadata File
---------------------------------------------

In order to configure SAML access to Airkit applications, the SAML Assertion Metadata must be generated from the **Identity Provider** (IdP) of choice. It will be used to share configuration credentials between the IdP and the **Service Provider** (SP). The IdP metadata usually contains the IdP certificate, the entity ID, the redirect URL, and the logout URL.

Uploading the SAML Metadata File
---------------------------------------------

This XML file needs to be uploaded in the app, and determines which IdP should be receiving the SAML request. This is done in the [Console](https://support.airkit.com/docs/console). Select Settings from the options on the left. Then, from the submenu, select Organization to find the Authentication section. In "Manage SAML Configurations," click the Create New button. 


[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/saml-authentication-v1714-0.png",
        "Screen Shot 2022-01-28 at 9.48.57 AM.png",
        1879,
        304,
        "#fdfdfd"
      ]
    }
  ]
}
[/block]
Click on the dialog box located on the right side of the screen and manually upload the XML file, or simply drag and drop it to begin the upload instantly. Finally, press Create in order to generate the SAML configuration.
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/saml-authentication-v1714-1.png",
        "Screen Shot 2022-01-28 at 9.50.08 AM.png",
        396,
        326,
        "#fcfcfc"
      ],
      "sizing": "smart"
    }
  ]
}
[/block]
Connecting Your Application with the Metadata
---------------------------------------------

Next, go to your application in the studio, and go to [Configuration Builder](https://support.airkit.com/docs/configuration-builder).  Under the Global section, change the **App Authentication Type** to **Secure App**, and make sure the **Authentication Method** is set to **Custom**. Finally, click the drop down under SAML and select the XML uploaded in the previous step. 
[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/saml-authentication-v1714-2.png",
        "Screen Shot 2022-01-25 at 5.14.17 PM.png",
        2156,
        1358,
        "#fcfcfc"
      ]
    }
  ]
}
[/block]
Connecting the IdP to the Application
---------------------------------------------

Once you have completed the content of the application, save your changes and click Publish in the top right hand corner of the studio. Be sure to copy the link that users will utilize to access their application. 

 This is the URL that your IdP should redirect users back to after they authenticate, and this is called something different in each IdP. Okta calls it “Single Sign On URL,” Auth0 calls it the “Application Callback URL,” and OneLogin calls it the “ACS (Consumer) URL,” to name a few examples. Please refer to the documentation and settings for your specific IdP for where to input this URL.

After publishing your application and saving the URL to the IdP, users should be redirected to authenticate before using the application.