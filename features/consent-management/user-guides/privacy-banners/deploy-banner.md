---
description: Options to generate and deploy banner.
---

# Deploy Banner

`Sources > Privacy banners ( tab GENERATE & DEPLOY)`

## Generate Banner Versions

To deploy a new or updated banner it is first necessary to generate a new version of the banner. Click `GENERATE` to open the modal dialogue.

<figure><img src="../../../../.gitbook/assets/image (214).png" alt=""><figcaption></figcaption></figure>

You will have following option when generating a new container version.

| Option                 | Description                                                                                                                                                         |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Comment**            | You can provide a comment to document the changes of the new banner version (e.g. change text of accept button).                                                    |
| **Reactivate privacy** | In case you check this option **all visitors of the website will be re-asked for consent, they will again see the banner when visiting the website the next time.** |

## Preview New Banner Versions

You can preview and test new banner versions by clicking the `TEST` option on the right site of the banner version in the banner version list. This will preview the banner on a demo website.

{% hint style="info" %}
It is recommended to test new banner on a test environment of the real website before deploying it.
{% endhint %}

## Banner Deployment Options

The deployment process of a new banner version varies depending on the selected hosting method of the privacy banner. You can select the hosting method of a banner in the privacy banner settings that can be accessed with the `gear` icon on the top left of the interface (beside the privacy banner name).

### **Commanders Act CDN**

Commanders Act CDN ensures a reliable and performant hosting of your banner. It allows to deploy banners automatically and in real-time.

<figure><img src="../../../../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>

Click `DEPLOY` to deploy a banner to the Commanders Act CDN.

<figure><img src="../../../../.gitbook/assets/image (211).png" alt=""><figcaption></figcaption></figure>

### **On premise (self-hosted)**

This option allows to self-host privacy banner. It therefore requires manual effort on each update. For on premise hosting it is necessary to provide the URL of the folder where the on premise banner is hosted. Example:

`http(s)://www.mydomain.com/myfolder/`

<figure><img src="/broken/files/gHiKp3slHZo7BtZDBRqf" alt=""><figcaption></figcaption></figure>

Click `DOWNLOAD` to download on the right side of the new banner files and manually update them on your server.

<figure><img src="../../../../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>

## Container vs. Banner Deployment

In case both TMS and Consent Commanders Act are used to manage tags it is important to understand what needs to be generated and deployed for different update scenarios. Following table lists the elements that needs a generation and deployment for common scenarios.

| Scenario                                                                                                                           | Affected Web Container | All Web Container | Consent Banner |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | ----------------- | -------------- |
| Global options change (`Data Governance > Consent Management > Settings`)                                                          | Yes                    | Yes               | Yes            |
| Category or vendor is added, deleted or updated on a used banner                                                                   | Yes                    | Yes               | Yes            |
| Tag is added to a container (`Source > Web Containers`)                                                                            | Yes                    | No                | No             |
| Tag is assigned to a category or vendor in the used banner (`Data Governance > Consent Management > Categories (Tab ASSIGN TAGS)`) | Yes                    | No                | No             |
| Banner text or style change                                                                                                        | No                     | No                | Yes            |
| Banner button actions change                                                                                                       | No                     | No                | Yes            |

{% hint style="info" %}
On your website, don't forget to integrate a button or a link to allow your users to modify their consent choices

Use our Onsite API, command [consentCenter.show](../../onsite-api/consentcenter.show.md)
{% endhint %}
