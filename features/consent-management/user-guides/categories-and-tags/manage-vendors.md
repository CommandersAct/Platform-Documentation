---
description: Management of Commanders Act Consent vendors.
---

# Manage Vendors

`Data Governance > Consent Management > Vendors`

In this section you can manage your Commanders Act Consent vendors. These vendors will be used by your privacy center to provide users with detailed privacy management options.

## Vendors

{% hint style="info" %}
To enable native vendors go to `Data Governance > Consent Management >  Settings` and activate the custom vendors option.
{% endhint %}

Click `ADD VENDOR` to add vendors to your Commanders Act Consent installation. You can select vendors available on Commanders Act TMS (`Predefined Vendors`) or add custom vendors (`Custom Vendor`) by selecting the respective tab. A _Commanders Act_ vendor is available by default.

Each vendor can be mapped to Consent categories with the respective dropdown. This allows users to provide consent to all vendors of a category at once in the privacy center. A `PEN` icon allows to edit information of the vendor that is displayed in the privacy center. Following fields are available per vendor. A `TRASH` icon allows to remove the vendor.

| Option                             | Description                                                                                                                                                                                                                       |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**                           | Name of the vendor. Privacy centers will display this name.                                                                                                                                                                       |
| <p></p><p><strong>ID</strong> </p> | ID of the vendor. This ID is used in raw data exports and for technical setup of certain functionalities. It is possible to manually provide an ID. In case the field is left empty a category ID will be assigned automatically. |
| **Description**                    | Description of the vendor. Privacy centers use this description as the default description for this vendor in case no localisation was provided in the banner editor.                                                             |
| **Policy URL**                     | Privacy Policy Link of the vendor. Privacy centers display this URL for each vendor.                                                                                                                                              |

{% hint style="warning" %}
It is possible to map vendors to multiple categories for stand-alone installation of Commanders Act Consent. Tags in your Web Container can only be mapped to one category and vendor.&#x20;
{% endhint %}

{% hint style="info" %}
It is necessary to generate and deploy new version of Consent banners to deploy updates in the vendor section.
{% endhint %}

## IAB vendors

{% hint style="info" %}
Commanders Act is compliant with IAB TCF 2.2 ([Link to official listing](https://iabeurope.eu/cmp-list/)). To enable IAB vendors go to `Data Governance > Consent Management > Settings` and activate the IAB option.
{% endhint %}

Click `ADD IAB TCF 2.2 VENDORS` to manage the IAB vendors with your Commanders Act Consent installation. You can either select all vendors or select specific vendors that are relevant for your setup.

The description of IAB TCF 2.2 vendors is automatically loaded from the IAB TCF 2.2 framework.

Commanders Act Consent will automatically configures purposes, special purposes, features and special features in the `CATEGORIES` tab depending on the selected vendors.

<figure><img src="../../../../.gitbook/assets/image (188).png" alt=""><figcaption><p>Add IAB TCF 2.0 vendors popin </p></figcaption></figure>

## Google ACM vendors

{% hint style="info" %}
To enable Google ACM vendors go to `Data Governance > Consent Management > Settings` and activate the IAB option **and** the Google ACM vendors.
{% endhint %}

Google [Additional Consent Mode](https://support.google.com/admanager/answer/9681920?hl=en) (ACM) allows to manage consent for Google Ad Technology Providers (ATP) (that are not part of the IAB TCF Global Vendors List) alongside IAB TCF vendors.

`Add Google ACM vendor` allows to add Google ACM vendors to add a Google ATP to your Commanders Act Consent installation. Each vendor has to be mapped to a TrustCommander category.

Descriptions for the ATP that are shown in the Consent banner (into the privacy center) are automatically loaded from the Google ACM list.

Google ACM vendor management only works with IAB TCF 2.0 & 2.2 banner templates.
