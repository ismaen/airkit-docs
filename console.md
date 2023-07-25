The Airkit console is the part of the platform provides access to [Org](https://support.airkit.com/docs/airkit-organizations)-level material, making it possible to configure application resources, connect external integrations, and access all applications that have been created within the relevant Organization.

On the leftmost side of the console is the Tree, which allows you toggle between different tabs within the Console. The contents of the selected section is displayed in the Stage to the immediate right of the Tree. Clicking on individual elements within the Stage opens the Inspector, which displays more details about the element being inspected:


![2021-10-04_17-30-22.png](./assets_v1714/console-v1714-0.png)


# Structure of the Stage


While the layout of the Stage varies depending on which section has been selected, there are some features that remain whenever applicable. This section discusses what they are and how to use them.


## 'Create New' Button


Many tabs have a 'Create New' Button in the upper right:

<img src="./assets_v1714/console-v1714-1.png" alt="organizing info" style="max-width: 100px; width:100%"/>

Clicking this button opens the Inspector, which provides the interface to create a new instance of the the tab-relevant item. For instance, if the *Apps* tab is open, this button creates a new app, whereas if the *Resources* tab is open, this button creates a new resource.


## Organizing Information


To the upper left of the Stage is the search bar and the 'Sort' button. If present, the 'Filter' button will rest between them:


<img src="./assets_v1714/console-v1714-2.png" alt="organizing info" style="max-width: 250px; width:100%"/>



These make it possible to explore and organize the items stored under a particular tab. 


* **Search** - Search for an item by name
* **Filter** - Filter items so that only items with a specified traits will appear in the Stage
* **Sort** - Sort items according to the value held in a particular column.


The effects of the 'Sort' button can be replicated by clicking directly on the column name:


![2021-10-04_17-38-11__1_.gif](./assets_v1714/console-v1714-3).gif)


# Tabs



## Apps

**Creates and accesses all the apps associated with the relevant Organization.**


Clicking anywhere on the row designating an app opens up the Inspector, where you can view the app's status, edit the app's name or description, open the app in the Studio, or even delete it.


![2021-10-04_17-41-07__1_.gif](./assets_v1714/console-v1714-4).gif)


This is the section that will be opened automatically upon logging into an Organization.


## Activity

**Views the logged Events and metrics associated with all of the Organization's apps.**


To view metrics associated with a particular app, select it from the dropdown menu on the upper right:


![2021-10-04_17-46-20__1_.gif](./assets_v1714/console-v1714-5).gif)


There is no 'Create New' button under **Activity**. This section of the console is not meant to be part of building directly; it is meant to display data regarding what has already been built.


## Datastores

**Views a list of the [Datastores](https://support.airkit.com/docs/datastores) connected to your Organization.**


Clicking on one opens the Inspector, which displays information regarding which apps reference the Datastore, as well as the schema of the [App Objects](https://support.airkit.com/docs/airdata-app-objects) stored within.


![2021-10-04_17-50-15__1_.gif](./assets_v1714/console-v1714-6).gif)


Using this information, it is possible to share custom data objects between different applications in your organization.


There is no 'Create New' button under **Datastores**. Creating a new Datastore must be done in the [Studio](https://support.airkit.com/docs/studio), in the Data Builder.

## Integrations 

**Defines connections with the outside world.**


This is the section you'll use to configure how external data sources will be authenticated. Once authenticated, you can use it across your applications, whether as part of an HTTP request, a [control](https://support.airkit.com/reference/web-controls-overview), or a [Data Operation](https://support.airkit.com/reference/the-salesforce-data-operation).


There are two subcategories under *Integrations*: **Connected Accounts** and **Custom Integrations**.


### Connected Accounts 

**Provides credentials that allow you to integrate with a configured external source.**


Connected accounts can be used to create connections in [Connection Builder](https://support.airkit.com/docs/connection-builder) that retrieve or send data to these connected accounts.


Out-of-the-box, Airkit with common external sources, such as [Stripe](https://support.airkit.com/docs/creating-a-stripe-integration) and [Twilio](https://support.airkit.com/docs/connecting-your-twilio-numbers-to-airkit), preconfigured. Custom external sources can also be added in the **Custom Integrations section,** see below.


### Custom Integrations

**Configures external sources.**


These external sources can be accessed under *Connected Accounts*(see above) to provide credentials for a particular account. The process of using a custom integration is first defining what the integration should look like in the custom integrations section and then adding a credential for the integration in the Connected Accounts section.


Currently supported custom integrations are:


* *OAuth 2.0* - Use OAuth and configure all the needed properties.
* *API Token -* Standard API token implementation.
* *HTTP - Basic Auth* Basic Username and password HTTP Auth.
* *Custom Token* - Specify custom parameters to retrieve a token.
* *SFTP* - Specify a username and password or private key for authentication.


## Resources 

**Connects to specific external resources like phone numbers and web domains.**


This is where you'll define the external resources used to interface directly we app users, such as:


* Phone Numbers - used to send and receive [calls](https://support.airkit.com/docs/building-a-simple-voice-bot) and [text messages](https://support.airkit.com/docs/building-a-simple-chat-bot).
* Domains - define the web domain of links to Airkit web apps.
* Embeds - defines the means to [embed published Airkit apps into existing web pages](https://support.airkit.com/docs/airkit-embeds).


Note that this is not where you will designate what app you want to associate these resources with; that must be done by accessing the app itself in the [Studio](https://support.airkit.com/docs/studio), within the Configuration Builder.


For more on adding and modifying resources, check out [this article](https://support.airkit.com/docs/adding-and-modifying-resources). 


## API

**Tells external sources how to recognize and authenticate your apps.**


The *I*ntegrations** and **Resources** sections tell your apps how to recognize and authenticate external sources. The **API** section tells external sources how to recognize and authenticate your Airkit apps. This is primarily done in two ways: **tokens** and **web hooks**.


### Tokens 

**Creates and views web tokens as needed.**


Tokens will be displayed only at the time of creation. You will be able to use this token when connecting between external resources and Airkit with an Airkit App API. It is also possible to connect multiple Airkit Apps together in this fashion. 


For a more detailed walkthrough of how create and use tokens, check out [Securing API Endpoints with Airkit API Tokens Permissions](https://support.airkit.com/docs/securing-api-endpoints-with-airkit-api-tokens-and-permissions).


### Webhooks 
** Configures Webhooks **


Webhooks are used to create datasources and resources in your [Organization](https://support.airkit.com/docs/airkit-organizations). 


## Settings


Modify settings pertaining directly to your account, Organization, and security. Note that not every role has the needed permissions to access every one of the following subsection; for more on the permissions given to each type of user, check out [Managing User Roles](https://support.airkit.com/docs/managing-user-roles).


### Users


This section provides a list of active users in the Organization and describes their login information and role. 


### Invites


Add a new user to an Organization, if applicable (as only users with the appropriate permissions will be able to invite new users).


When inviting a new user, selecting the *SSO Only* checkbox will use the user’s Google OAuth credentials (if applicable) to log in. The user can log in using an assigned username and get to set a password themselves. If a username is not assigned, the invited user will be allowed to set their own.


For more on this section, check out [Adding Users to Airkit](https://support.airkit.com/docs/adding-users-to-airkit).


### Organization


View and modify information related directly to your Organization, including how your Org appears on the platform and the authorization credentials required to access it.


### Logs & Notifiers


Specify Organization-level notifications and logs. Logs can be stored in an S3 bucket. Notifiers can send alerts via Slack, email, or a custom Webhook when n app produces an error.


### Encryption Keys


Create and manage encryption keys. For more on how to create and use encryption keys, check out [Encrypting Data](https://support.airkit.com/docs/encrypting-data).


### My Account


View your account and security information.