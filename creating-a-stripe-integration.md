[Stripe](https://stripe.com/) is a payment processor. In order to collect payments from users, it is possible to use a Stripe Integration to collect funds. The Stripe integration requires a Stripe account. 


Getting the Stripe key
----------------------


Log into a Stripe Account. On the dashboard menu, make sure that the **Viewing test data** toggle is on. This will enable the configuration of a test stripe connection.

<img src="./assets_v1714/creating-a-stripe-integration-v1714-0.png" alt="organizing info" style="max-width: 250px; width:100%;"/>

Select the **Developers** option just above the toggle. Select **API Keys** from the developer menu. Ensure that the **Test Data** toggle is switched in the upper right. Click the button to reveal the secret key. Copy the key.


<img src="./assets_v1714/creating-a-stripe-integration-v1714-1.png" alt="organizing info" style="max-width: 450px; width:100%;"/>


Creating the Integration
------------------------


Log into [Console](https://support.airkit.com/docs/console). In console go to *Integrations > Connected Accounts.* Click on the *New* button in the top right corner. Select type **Stripe** from the dropdown list.

<img src="./assets_v1714/creating-a-stripe-integration-v1714-2.png" alt="organizing info" style="max-height:200px"/>

Give the Stripe Integration a name that will help identify the account it is tied to. It is possible to do multiple Stripe Integrations. This is particularly useful for a development and production level key. Paste the copied key from the Stripe Account into the API Token box. Save the integration.


Configuring an App to use the Integration
-----------------------------------------


Go to an App. Click on Configuration Builder. Scroll down to **Integrations** and select **New.**


<img src="./assets_v1714/creating-a-stripe-integration-v1714-3.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

Select Stripe from the dropdown under **Adapters** and then the Stripe Integration previously created. Now it is possible to select this Integration in the [Credit Card Web Control](https://support.airkit.com/reference/credit-card-web-control).