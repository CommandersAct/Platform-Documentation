---
description: Format of the Commanders Act Consent cookie.
---

# Consent Cookie



{% hint style="warning" %}
The [Consent Object](consent-object.md) received via the onsite API is now the official way to access the consent settings of Commanders Act Consent with JavaScript. The direct usage of the consent cookie is deprecated.
{% endhint %}

Commanders Act Consent stores the consent of website visitors in a 1st party cookie.

This article only explains the consent cookie. [Here](https://doc.commandersact.com/configure/cookies) you can find a list of all Commanders Act Consent cookies.

## Name

The default name of the consent cookie is `TC_PRIVACY`. It can be configured in `Data Governance > Consent > Settings`.

## Domain

The cookie is set as a 1st party cookie. The subdomain/domain of the cookie can be configured in `Data Governance > Consent > Settings`

## Value

The value consist of multiple fields separated by `@` symbols. The separator can be configured in `Data Governance > Consent > Settings` .

{% hint style="warning" %}
The consent cookie format is not 100% guaranteed to stay stable. We try to keep the format as stable as possible and extend it with "append only approach (adding new information with a new `@`)", but changes might happen in the unforeseeable future due to limited storage space in cookies.
{% endhint %}

The cookie value follows following pattern (optional elements are wrapped in `[]`).&#x20;

`<status>@<privacy_version>[|<tcf_version>]|<banner_id>|<site_id>@<consent_categories>@<blocked_on_categories>@<updated_timestamp>,<creation_timestamp>,<to_expire_timestamp>[@<tcf_vendor_consent_string>]`

| Field                         | Description                                                                                                                                                                                                                                                                                                                                                  | Example Value                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| `<status>`                    | Status that indicates if a visitor provided his optin or optout.                                                                                                                                                                                                                                                                                             | <p><code>1</code>: Visitor is optout</p><p><code>0</code>: Visitor is optin</p> |
| `<privacy_version>`           | Version of the privacy banner the visitor interacted with.                                                                                                                                                                                                                                                                                                   | `008`                                                                           |
| `<tcf_version>`               | Version of the IAB TCF framework. Only available in case IAB is activated for the account and an IAB banner is used to manage consent. It follows this format:`<tcf_global_vendor_list_specification_version>\|<tcf_policy_version>\|<tcf_global_vendor_list_version>`                                                                                       | `2\|2\|42`                                                                      |
| `<banner_id>`                 | ID of the privacy banner the visitor interacted with.                                                                                                                                                                                                                                                                                                        | 12                                                                              |
| `<site_id>`                   | ID of the site in the Commanders Act Platform.                                                                                                                                                                                                                                                                                                               | 34                                                                              |
| `<consent_categories>`        | Comma-separated-list of optin, or optout categories. Meaning depends on `<status>` field. E.g. when `<status>` is `0` then the visitor provides consent for the listed categories. The value is URL encoded. Therefore the comma separator is replaced with `%2C`. Some old banner versions might have the value `ALL` in case all categories are opted out. | `2%2C12%2C13`                                                                   |
| `<blocked_on_categories>`     | Comma-separated-list of blocked on categories.  The value is URL encoded. Therefore the comma separator is replaced with `%2C`.  These categories are not repeated in the `<consent_categories>` field.                                                                                                                                                      | `2%2C12`                                                                        |
| `<updated_timestamp>`         | UNIX timestamp for when the consent was last updated                                                                                                                                                                                                                                                                                                         |                                                                                 |
| `<creation_timestamp>`        | UNIX timestamp in milliseconds when the consent was provided.                                                                                                                                                                                                                                                                                                | `1592900933049`                                                                 |
| `<to_expire_timestamp>`       | UNIX timestamp for when the consent will expire                                                                                                                                                                                                                                                                                                              |                                                                                 |
| `<tcf_vendor_consent_string>` | Vendor consent information (e.g. for IAB TCF vendors).   Only available when vendors are activated for the account and in case vendors are used in the banner. The value is compressed and encoded to keep the cookie size small.                                                                                                                            | `AAAAAjkb23...`                                                                 |

## Examples

### Example1: Optin for some categories

`0@002|12|3441@1%2C3@4@1592900933049@1592900933049`

| Field           | Description                                         |
| --------------- | --------------------------------------------------- |
| `0`             | Visitor is optin.                                   |
| `002`           | Visitor provided optin on banner version 002.       |
| `12`            | Banner ID is 12.                                    |
| `3441`          | Site ID is 3441.                                    |
| `1%2C3`         | Visitor provided optin for categories 1 and 3.      |
| `4`             | The category 4 is blocked on.                       |
| `1592900933049` | Visitor provided optin on Tue Jun 23 2020 08:28:53. |

### Example 2: Optout for all categories

`1@012|26|4221@@4@1592900933049@1592900933049`

| Field           | Description                                          |
| --------------- | ---------------------------------------------------- |
| `1`             | Visitor is optout                                    |
| `012`           | Visitor provided optin on banner version 012.        |
| `26`            | Banner ID is 26.                                     |
| `4221`          | Site ID is 4221.                                     |
|                 | Visitor provided optout to all categories.           |
| `4`             | The category 4 is blocked on.                        |
| `1592900933049` | Visitor provided optout on Tue Jun 23 2020 08:28:53. |



{% hint style="info" %}
Good to know: special characters such as "@" or "|" are encoded in the cookie value\
%2C = ","\
%7C = "|"\
%40 =  "@"
{% endhint %}

