The previous article discussed what Journeys are and how they allow a user's progress to be tracked and saved. Here, we take a deeper dive into how to apply the concept of Journeys by examining them in the context of starting, continuing, and identifying Journeys through web apps.

# Starting Links and Canvas Links

Interacting with a web app requires navigating to a particular URL. There are two categories of URL that can lead to an Airkit web app: **Starting Links** and **Canvas Links**.

A **Starting Link**, referred to as a "Web URL" in the Configuration Builder, triggers the start of a Journey. It can be used any number of times to begin any number of Journeys. 

A **Canvas Link**, sometimes also referred to as a "Journey Link", leads to the most recently accessed Web Page within an existing Journey. It is capable of doing so because it contains a unique Journey identifier in the URL path. 

## The Structure of Starting Links

The following is an example of a **Starting Link**, where "app.airkit.com" is the domain name of the application and {trigger} represents an automatically-generated, app-specific trigger:

```
https://app.airkit.com/l/{trigger}
```

An app-specific trigger is required because Airkit allows multiple applications to be as associated with a domain. However, while applications will use an automatically-generated trigger by default, it is also possible to create custom triggers. The following is an example of a **Starting Link**, where "app.airkit.com" is the domain name of the application and {custom_trigger} represents a customized, app-specific trigger:

```
https://app.airkit.com/c/{custom_trigger}
```
Setting custom triggers allows for the creation **Starting Links** that provide some intuitive understanding of what sort of application is being linked to. The automatically-generated trigger "5w" tells a potential user nothing about the app it links to, whereas the custom trigger "order_status" indicates that it links to an app that allows the user to check the status of their order.

For a nut-and-bolts walkthrough of how to create custom trigger (as well as how to set up a White Label domain), see [Connecting Your Domain to Airkit](doc:connecting-your-domain-to-airkit).

## The Structure of Canvas Links

The following is an example of a **Canvas Link**, where "app.airkit.com" is the domain name of the application and {id} represents a unique Journey identifier:

``` 
Example: https://app.airkit.com/u/{id}
```

Note that, for security purposes, the unique Journey identifier that appears in the **Canvas Link** is not the same as ```session.id```, the session-level variable used to identify Journeys internally. The {id} that appears in **Canvas Links** is a useful identifier only in the context of URLs.

# Applications

**Starting Links** are intended for general use; anyone can click on one and begin new Journey. It is the **Starting Link** you want to link to when providing a link to your application in any sort of public space, and, upon publishing an application, only **Starting Links** will be provided in the pop-up window.

**Canvas Links** are specific. They provide a means for app users to navigate away from their web Journey then return to continue where they left off. It is the **Canvas Link** you want to send to users in follow-up texts when you want to remind them to return to a half-finished Journey and finish what they started. The **Canvas Link** will bring them directly to the Web Page their Journey most recently navigated to, with all previously-saved progress, including the binding of variables, still intact.

<details>
  <summary>Are Canvas Links still used if a Journey does not begin with a Starting Link?</summary>

<br>

Journeys can start in many ways, and clicking on a **Starting Link** is only one of them. Journeys might also start, for instance, with an incoming text or phone call. Users will still be directed to a **Canvas Link**, not a **Starting Link**, to continue their Journey online.

As an example, consider call deflection, a common Airkit use case. A client calls in. They answer a few automated questions before receiving a text directing them to a web app that will help them achieve  their goal. Their flow through the web application should be part of the same Journey that they were on when answering those automated questions, so all relevant user information will be saved and accessible within a single Journey. This prevents users from having to repeat themselves and results in a better user experience. Thus, the text directing users to the web app contains a **Canvas Link**.

Note that **Canvas Links** only link to Web Pages that have be explicitly navigated to using the [Navigate To Web Flow](ref:navigate-to-web-flow-action) or [Navigate to Web Page](ref:navigate-to-web-page-action) Actions. One of these must be explicitly called upon before sending over a **Canvas Link**, or the **Canvas Link** will not lead to any Web Page at all.

</details>


Upon navigating to a **Starting Link** and beginning a Journey, the change from **Starting Link** to **Canvas Link** will be reflected in the address bar of the web browser, as an identifier becomes part of the path parameters. Should you endeavor to provide someone a link to an Airkit app, be mindful of which URL you are sending. You cannot send someone a **Starting Link** by copy/pasting the URL from your address bar, as the URL displayed will have already changed from a **Starting Link** to a **Canvas Link**.

<details>
  <summary>Can Starting Links and Canvas Links have different domains?</summary>

<br>

Yes, **Starting Links** and **Canvas Links** can have different domains, as they are configured separately in the [Configuration Builder](doc:configuration-builder). The web resource associated with **Starting Links** is configured under the **Web URLs** section, and the web resource associated with **Canvas Links** is configured under the **Journey Links** section. Note that web resources must be created in the **Domains** section of the [Console](doc:console) before they can be used in either **Starting Links** or **Canvas Links**.

</details>