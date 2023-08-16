---
description: >-
  Description of the Consent Object format that is used by the onsite API to
  receive and update consent.
---

# Consent Object

The Consent Object is a standardized way to represent consent throughout all methods of the onsite JavaScript API (similar to the IAB TCF consent string). The object holds a `meta` property that includes metadata like the validity of the cookie and a `consent` property that holds that current consent settings stored on the browser.The onsite API and Consent Object is the official way to access the consent settings of Commanders Act CMP with JavaScript. The direct usage of the [Consent Cookie](consent-cookie.md) is deprecated.

### Example Consent Object <a href="#example-consent-object" id="example-consent-object"></a>

```
{
    meta: {
        version: "1.0",
        tcfPolicyVersion: "2",
        siteId: "1234",
        bannerId: "12",
        bannerVersion: "50",
        consentId: "183049723840253",
        dateCreated: 1614174067000,
        dateUpdated: 1614185078030,
        dateExpires: 1614236789942
    },
    consent: {
        status: "all-on|all-off|mixed|unset",
        categories: {
            "1": {
                status: "on",
                required: true
            },
            "2": {
                status: "on|off|unset"
            },
            "tcf2_1": {
                status: "on|off|unset"
            },
            "tcf2_2": {
                status: "on|off|unset",
                legIntStatus: "on|off|unset"
            },
            "tcf2_sf_1": {
                status: "on|off|unset"
            }
        },
        vendors: {
          "1": {
                status: "on|off|unset"
          },
          "tcf2_1": {
                status: "on|off|unset"
          },
          "tcf2_2": {
                status: "on|off|unset",
                legIntStatus: "on|off|unset"
          },
          "acm_1": {
                status: "on|off|unset"
          }
        }
    }
}
```

### Meta Properties <a href="#meta-properties" id="meta-properties"></a>

The `meta` property includes metadata and context for the consent that was provided on a browser.

| Property                | Description                                                                        | Type   |
| ----------------------- | ---------------------------------------------------------------------------------- | ------ |
| `meta.version`          | Version of the Consent Object.                                                     | String |
| `meta.tcfPolicyVersion` | Version of the IAB TCF consent.                                                    | String |
| `meta.siteId`           | Commanders Act site id associated to the consent.                                  | String |
| `meta.bannerId`         | Banner id associated to the consent.                                               | String |
| `meta.bannerVersion`    | Banner version associated to the consent.                                          | String |
| `meta.consentId`        | Id of the consent stored in the `TCPID` cookie.                                    | String |
| `meta.dateCreated`      | Timestamp when the consent was provided (UNIX Epoch in Milliseconds).              | Number |
| `meta.dateUpdated`      | Timestamp when the consent was updated the last time (UNIX Epoch in Milliseconds). | Number |
| `meta.dateExpires`      | Timestamp when the consent will expire (UNIX Epoch in Milliseconds).               | Number |

### Consent Properties <a href="#consent-properties" id="consent-properties"></a>

The consent property includes detailed information about the consent provided on the browser.

| Property                                   | Description                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `consent.status`                           | Global status of the consent that can have one of the following values: **all-on:** All consent categories have been accepted.**all-off:** All consent categories have been refused (except blocked on).**mixed:** Some consent categories have been refused.**unset:** No consent has been provided yet.                                                              |
| `consent.categories[category_id].status`   | Status of an individual category:**on:** Consent was provided.**off:** Consent was rejected.**unset:** No consent has been provided yet (In case neutral button position is configured it will switch to neutral button position for this category).​`category_id` is the category id configured under `Data Governance > Consent Management > Settings > Categories`. |
| `consent.categories[category_id].required` | The property was set to blocked on and the status is always **on**.                                                                                                                                                                                                                                                                                                    |
| `consent.vendors[vendor_id].status`        | Status of an individual vendor:**on:** Consent was provided.**off:** Consent was rejected.**unset:** No consent has been provided yet (In case neutral button position is configured it will switch to neutral button position for this vendor).​`vendor_id` is the vendor id configured under `Data Governance > Consent Management > Settings > Vendors`.            |

Category and Vendor IDs are prefixed with an identifier in case they are managed by a consent framework.

| Framework | Prefix                                                                     |
| --------- | -------------------------------------------------------------------------- |
| `tcf2_`   | IAB TCF 2 framework. Special features are additionally prefixed with `sf_` |
| `acm_`    | Google's Additional Consent Mode vendors.                                  |

​
