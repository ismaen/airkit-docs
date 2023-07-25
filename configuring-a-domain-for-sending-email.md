Airkit provides two methods to configure email addresses for sending emails. Both involve configuration at an Organization Level. While the configuration of a single email address involves only email verification, configuring an entire domain (meaning any user at the domain can send email) is significantly more complicated.


Configuration of a domain requires adding DNS records. This article will walk through configuring the records, testing the records, and common issues.


Adding the DNS Records
----------------------


The first step is to create an Email Domain under Resources in [Console](https://support.airkit.com/docs/console). Enter the domain in the *Email Domain* field and click create. The resulting Inspector will show a button for "Open verification Instructions."


![Console-EmailDomain-DNSInstructions.png](./assets_v1714/configuring-a-domain-for-sending-email-v1714-0.png)


The TXT record at the top needs to be configured, propagated, and verified before the email can be sent from any address associated with this domain. DKIM or DomainKeys Identified Mail allows airkit to assign responsibility for email be sent through the system. More information about DKIM can be found in the [RFC](https://tools.ietf.org/html/rfc6376). In order to allow for that identification, additional CNAME records are required.


Once these records are created, it is possible to verify from the command line that the configuration is valid. Using the dig tool, copy the domain from the Setup Instructions dialog.



```
> dig -t TXT _amazonses.<<domain>>.com
```

Where **<<domain>>** is replaced with the domain name. Check the response **ANSWER SECTION** to confirm that the record returned matches the Configuration Instructions.


![Console-EmailDomain-DIGResponse.png](./assets_v1714/configuring-a-domain-for-sending-email-v1714-1.png)


The same can be done for the CNAME subdomains for DKIM.


Properties of an Email Domain Name
----------------------------------


In Console, when selected, an Email Domain the following properties.


### Name


Currently the same as the Remote ID, but is a text string to identify the resource.


### Remote ID


The valid domain for the email addresses.


### From Address


A list of email addresses created with the domain.


### Used In Deployments


List of deployments where the email is used.


### Capabilities


This will just be a block for Email Domain.


### Verification Status


Can be either "Pending", "Failed", or "Success". If it is Pending, it is in the process of checking that records have been configured correctly. Check common issues below or test with the **dig** command above. Success means that the email domain is ready for use.


Common Issues
-------------


**Verification Status Failed** - Verify that the DNS records are configured correctly. Some DNS providers will require the definition of the subdomain only and not the full **_amazonses.<<domain>>.com**. Try removing the **<<domain>>.com**part. Click the retry button under Verification Status.


**Verification Status Pending** - DNS takes time to propagate. It can take up to 72 hours for a domain to fully confirmed. Please give it some time before reaching out to support at airkit.


Further Reading
---------------


* [Sending Email from Airkit](https://support.airkit.com/docs/sending-email-from-airkit) - for a more comprehensive guide on how to send an email.
* [The Send Email Data Operation](https://support.airkit.com/reference/the-send-email-data-operation) - for specifics about the send email data operation.
* [Configuration Builder](https://support.airkit.com/docs/configuration-builder) - for information on setting up integrations like email.