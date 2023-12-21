---
description: >-
  Following you will find information and setup instructions for SAML based
  Single Sign-On with Commanders Act.
---

# Single Sign-On

## Overview

Commanders Act supports SAML 2.0 based Single Sign-On authentication and authorization.&#x20;

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Swimlane diagram of the Single Sign-On functionality.</p></figcaption></figure>

## Setup

To setup Single Sign-On Commanders Act requires the metadata.xml of the IDP or following information:

* Single Sign-In Endpoint
* Single Sign-Out Endpoint
* EntityId of the IDP
* Public key of the IDP (X509 certificate)

Please contact a Commanders Act consultant to initiate the setup. You will then receive a namespace parameter `<name>` and the site id `<id_site>` used in following SAML Endpoints and SAML Attributes.

### SAML Endpoints

Following you will find an overview of the SAML API endpoints used by Commanders Act.&#x20;

**ACS URL/Endpoint URL** \
https://platform.commandersact.com/saml2-acs/\<name>

**Login URL** \
https://platform.commandersact.com/saml/\<name>

**SP Entity ID/Partner's Realm**\
commanders-act

### SAML Attributes

Following SAML attributes are currently supported. It is required to send the email attribute.&#x20;

| Attribute                  | Description          | Type                                                                                                                                                                      |
| -------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| firstname                  | User first name      | optional, default empty ''                                                                                                                                                |
| lastName                   | User last name       | optional, default empty ''                                                                                                                                                |
| email                      | User email           | required                                                                                                                                                                  |
| companyName                | Company name         | optional, default empty ''                                                                                                                                                |
| jobTitle                   | Job title            | optional, default empty ''                                                                                                                                                |
| mobileNumber               | Mobile phone number  | optional, default empty ''                                                                                                                                                |
| lang                       | User language code   | optional, default empty ''                                                                                                                                                |
| commandersact\_\<id\_site> | Applied user profile | <p>optional, Possible values:</p><ul><li>administrator</li><li>technical</li><li>marketing</li><li>custom</li><li>readOnly</li><li>partnerAdmin</li><li>partner</li></ul> |

## FAQ

**How long is the SAML session duration?**\
1440 seconds.

**Which protocol is used for Single Sign-On?**\
SAML 2.0
