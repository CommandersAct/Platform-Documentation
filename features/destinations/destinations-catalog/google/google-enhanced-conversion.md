---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Google Enhanced Conversions

[Google](https://about.google/) is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. Using the [Data Manager API](https://developers.google.com/data-manager/api), you can use the [enhanced conversions](https://support.google.com/google-ads/answer/9888656) feature to send your conversion events enriched with first-party data. Google uses this additional data to improve the reporting of your online conversions driven by ad interactions.\
Enhanced conversions supplement your existing conversion tags. They send hashed first-party conversion data from your website to Google in a privacy-safe way.

{% hint style="info" %}
You must complete the [setup and configuration steps](https://support.google.com/google-ads/answer/11062876) in Google Ads before you can send enhanced conversions to Google.
{% endhint %}

## Key features

The Google Enhanced Conversions destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports the Google method [events.ingest](https://developers.google.com/data-manager/api/reference/rest/v1/events/ingest), so your data is bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic normalization and hashing**: user identifiers are automatically normalized and hashed (SHA-256) to match [Google's formatting requirements](https://developers.google.com/data-manager/api/devguides/concepts/formatting).
* **Smart mapping**: data mapping can be readjusted using the fields defined in your datalayer.
* **Batch mode**: events are always grouped and sent to Google in batches (multiple events per request). This keeps your traffic within the Data Manager API quota limits (see [Destination setup](google-enhanced-conversion.md#destination-setup)).
* **Consent signals**: Google consent values (`adUserData` and `adPersonalization`) are forwarded with each event.
* **Privacy-safe IP handling**: the device IP address is automatically excluded for users located in the EEA, the UK and Switzerland. This exclusion relies on the `User Country` field: if no country is provided, the IP address is sent to Google (see [Field mappings](google-enhanced-conversion.md#field-mappings)).
* **Cart data**: item-level data (Merchant Center product IDs, quantities, prices) can be sent alongside your conversions.

## Destination setup

{% hint style="warning" %}
In [Google Ads](https://ads.google.com/), you must complete the following actions:\
• Accept <mark style="color:blue;">`Customer data terms`</mark> under <mark style="color:blue;">`Goals`</mark> → <mark style="color:blue;">`Conversions`</mark> → <mark style="color:blue;">`Settings`</mark>\
• Flag <mark style="color:blue;">`Turn on enhanced conversions`</mark> under <mark style="color:blue;">`Goals`</mark> → <mark style="color:blue;">`Conversions`</mark> → <mark style="color:blue;">`Settings`</mark> → <mark style="color:blue;">`Enhanced conversions`</mark>.\
Review [Updates to your enhanced conversions settings](https://support.google.com/google-ads/answer/11062876) to learn more about turning on enhanced conversions.
{% endhint %}

{% hint style="info" %}
**Data Manager API vs. Google Ads API**\
The **Data Manager API** is Google's newer, unified API for sending advertiser data to Google's advertising products. It is the method **recommended by Google**, which provides an official [upgrade guide](https://developers.google.com/data-manager/api/devguides/events/google-ads/offline/upgrade#conversion-adjustments) for moving conversion uploads from the Google Ads API. We recommend using it for all new and existing setups.

The API used by this destination depends on your connector credentials. Please follow our [Migration to Data Manager API](https://doc.commandersact.com/features/destinations/destinations-catalog/google/migration-to-data-manager-api) guide to upgrade your credentials.\
• If your Google Ads credentials include the **Data Manager API** permission, events are sent with the Data Manager API method `events.ingest`. This page is mainly focused on the Data Manager API.\
• Otherwise, events are sent as conversion adjustments with the Google Ads API method `customers.uploadConversionAdjustments`. See[ Google Ads API (legacy)](google-enhanced-conversion.md#google-a-ds-api-legacy).\
Several settings and fields are marked **Data Manager API only**. They are ignored when the Google Ads API is used.\
The two APIs also have different requirements for user identifiers. See [Field mappings](google-enhanced-conversion.md#field-mappings).
{% endhint %}

{% hint style="info" %}
**Batch mode and quota limits**\
This destination works in batch mode, with certain exceptions: multiple events are packed into a single request to Google rather than sent one by one. Batching is required to stay within the quota limits of the Data Manager API.\
These limits apply to the number of requests, not the number of events. Grouping events into batches allow you to send high event volumes without reaching them.
{% endhint %}

{% hint style="info" %}
Your user account needs admin rights in the [Google Ads account](https://ads.google.com/intl/en/home/tools/manager-accounts/) where the conversion action is located. If your credentials are linked to a manager account (MCC), the manager account is automatically used as the login account.\
When available, this destination also includes the [`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en) value. It uses the **Google Click Identifier** Smart Mapping field first, then looks for the following cookies in this priority order:

1. `_gcl_aw`
2. `_gcl_dc`
3. `_gac_[GA_PROPERTY_ID]` (only if `Google Analytics Property Id` is set)
{% endhint %}

{% hint style="info" %}
Google Ads reports show the updated values after **24/48 hours**. For example, you can check <mark style="color:blue;">`Goals`</mark> → <mark style="color:blue;">`Conversions`</mark> → <mark style="color:blue;">`Summary`</mark> → <mark style="color:blue;">`View all conversion actions`</mark> → select your conversion action → <mark style="color:blue;">`Web pages`</mark>, and look at the column <mark style="color:blue;">`All conv. value`</mark>.
{% endhint %}

### Configuration

| Settings                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Authentication`                     | <p><em><strong><code>Required</code></strong></em><br>Your Google Ads credentials as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code>.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `Mapping`                            | <p><em><strong><code>Required</code></strong></em> <strong>[1]</strong><br>Map the Google Ads conversion actions where enhanced conversions are applied to your events by setting the fields <code>Conversion Action Name</code> and <code>Your event name</code>. Conversion action names can be found in the Google Ads interface following: <code>Goals</code> ➜ <code>Conversions</code> ➜ <code>Summary</code> ➜ <code>View all conversion actions</code> (or <code>+ Create conversion action</code> to create new ones). At least one line is required if you don't set the Smart Mapping field <code>Conversion Action Id</code>. Events that match no line are filtered. If a conversion action name can't be found in your Google Ads account, the event is rejected.</p> |
| `Custom Variables`                   | <p><strong>Data Manager API only.</strong><br>Send <a href="https://developers.google.com/data-manager/api/reference/rest/v1/events/ingest#CustomVariable">custom variables</a> related to events or items by setting the <code>Custom variable name</code> and <code>Your value</code>:<br>• <strong>Event-level</strong>: select <code>Default</code> in <code>Your option</code>. The content of <code>Your value</code> is sent as is.<br>• <strong>Item-level</strong>: select <code>In [Item List].X</code> or <code>In [Item List].X.product</code>, depending on where the property is located in your <code>Item List</code>, and set <code>Your value</code> with the property name. The value is read from each item.</p>                                                |
| `Google Analytics Property Id`       | The GA tracking ID, a string like `UA-XXXXXX-Y`, or `G-XXXXXXXXXX` for Google Analytics 4. It's used as an alternative method to retrieve the `gclid` from the `_gac_[GA_PROPERTY_ID]` cookie. See Destination setup for more details.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `Validate only`                      | <p><strong>Data Manager API only.</strong><br>For testing purposes. When checked, Google validates the request but doesn't record the events. Only errors are returned. Uncheck it before going live.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `Show errors on missing identifiers` | <p><strong>Data Manager API only.</strong> Checked by default.<br>When checked, events without the required user identifiers (see Field mappings) are reported as <strong>rejected</strong>. When unchecked, they are reported as <strong>filtered</strong>, which keeps your error reports focused on real issues.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

{% hint style="info" %}
**1.** Enhanced conversions must be enabled for your conversion action. In the Google Ads interface, click the conversion action ➜ expand `Enhanced conversions` ➜ flag `Turn on enhanced conversions` ➜ select `API`.
{% endhint %}

## Quick reference

<table><thead><tr><th width="388">Commanders Act Events</th><th>Google Tracking</th></tr></thead><tbody><tr><td><code>[Any Event]</code> <strong>[1]</strong></td><td><code>events.ingest</code> (Data Manager API)<br><code>customers.uploadConversionAdjustments</code> (Google Ads API, legacy)</td></tr></tbody></table>

{% hint style="info" %}
**1.** See `Mapping` in [Configuration](google-enhanced-conversion.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="warning" %}
**User identifiers: requirements depend on the API used**

**Data Manager API**: at least one of the following must be provided:

1. `User Email`, or
2. `User Phone`, or
3. `User First Name`, `User Last Name`, `User ZIP Code` and `User Country` (all four fields set).

An address is sent only if all four of its fields are set. Providing only some of them (e.g. first name and country) isn't enough.

**Google Ads API (legacy)**: a single identifier is enough. See [Google Ads API (legacy)](google-enhanced-conversion.md#google-a-ds-api-legacy) for more details.
{% endhint %}

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.\
Google properties are set in <mark style="color:blue;">`destinations.X`</mark> or <mark style="color:blue;">`events.X`</mark>. See the notes below the table for the exact path of each property.
{% endhint %}

<table><thead><tr><th width="293">Smart Mapping Fields</th><th>Commanders Act Default Properties</th><th>Google Properties</th></tr></thead><tbody><tr><td><code>Conversion Action Id</code><br><code>-</code></td><td><code>partners.google.conversion_action_id</code><br><code>Mapping</code> ➜ <code>Conversion Action Name</code></td><td><code>productDestinationId</code> <strong>[*][1][2]</strong><br><code>reference</code> <strong>[2]</strong><br><code>destinationReferences</code> <strong>[3]</strong></td></tr><tr><td><code>-</code></td><td><code>Authentication</code></td><td><code>operatingAccount.accountId</code> <strong>[*][2]</strong><br><code>loginAccount.accountId</code> <strong>[2][4]</strong></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>transactionId</code> <strong>[*][3]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>eventTimestamp</code> <strong>[*][3][5]</strong></td></tr><tr><td><code>Event Source</code></td><td><code>partners.google.event_source</code></td><td><code>eventSource</code> <strong>[3][6]</strong></td></tr><tr><td><code>Transaction Value</code></td><td><code>value</code></td><td><code>conversionValue</code> <strong>[3]</strong></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>currency</code> <strong>[3][7]</strong></td></tr><tr><td><code>Conversion Count</code></td><td><code>partners.google.conversion_count</code></td><td><code>conversionCount</code> <strong>[3]</strong></td></tr><tr><td><code>User Email</code></td><td><code>user.email</code><br><code>user.email_sha256</code></td><td><code>emailAddress</code> <strong>[8][9]</strong></td></tr><tr><td><code>User Phone</code></td><td><code>user.phone</code></td><td><code>phoneNumber</code> <strong>[8][9]</strong></td></tr><tr><td><code>User First Name</code></td><td><code>user.firstname</code></td><td><code>address.givenName</code> <strong>[8][9]</strong></td></tr><tr><td><code>User Last Name</code></td><td><code>user.lastname</code></td><td><code>address.familyName</code> <strong>[8][9]</strong></td></tr><tr><td><code>User Country</code></td><td><code>user.country</code></td><td><code>address.regionCode</code> <strong>[8][10]</strong></td></tr><tr><td><code>User ZIP Code</code></td><td><code>user.zipcode</code></td><td><code>address.postalCode</code> <strong>[8][10]</strong></td></tr><tr><td><code>Consent adUserData</code></td><td><code>partners.google.consent_ad_user_data</code></td><td><code>consent.adUserData</code> <strong>[3][11]</strong></td></tr><tr><td><code>Consent adPersonalization</code></td><td><code>partners.google.consent_ad_pers</code></td><td><code>consent.adPersonalization</code> <strong>[3][11]</strong></td></tr><tr><td><code>Google Click Identifier</code><br><code>-</code><br><code>Google Analytics Property Id</code></td><td><code>partners.google.gclid</code><br>Cookies <code>_gcl_aw</code>, <code>_gcl_dc</code><br>Cookie <code>_gac_[GA_PROPERTY_ID]</code></td><td><code>gclid</code> <strong>[12]</strong></td></tr><tr><td><code>WBRAID</code></td><td><code>partners.google.wbraid</code></td><td><code>wbraid</code> <strong>[12]</strong></td></tr><tr><td><code>GBRAID</code></td><td><code>partners.google.gbraid</code></td><td><code>gbraid</code> <strong>[12]</strong></td></tr><tr><td><code>Session Attributes</code></td><td><code>partners.google.session_attributes</code></td><td><code>sessionAttributes</code> <strong>[12]</strong></td></tr><tr><td><code>Device User Agent</code></td><td><code>context.device.user_agent</code></td><td><code>userAgent</code> <strong>[13]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>ipAddress</code> <strong>[13][14]</strong></td></tr><tr><td><code>Device Category</code></td><td><code>partners.google.device_category</code></td><td><code>category</code> <strong>[13]</strong></td></tr><tr><td><code>Device Browser</code></td><td><code>partners.google.browser</code></td><td><code>browser</code> <strong>[13]</strong></td></tr><tr><td><code>Device Browser Version</code></td><td><code>partners.google.browser_version</code></td><td><code>browserVersion</code> <strong>[13]</strong></td></tr><tr><td><code>Device Operating System</code></td><td><code>context.device.os.name</code></td><td><code>operatingSystem</code> <strong>[13]</strong></td></tr><tr><td><code>Device Operating System Version</code></td><td><code>context.device.os.version</code></td><td><code>operatingSystemVersion</code> <strong>[13]</strong></td></tr><tr><td><code>Device Screen Height</code></td><td><code>context.device.screen.height</code></td><td><code>screenHeight</code> <strong>[13]</strong></td></tr><tr><td><code>Device Screen Width</code></td><td><code>context.device.screen.width</code></td><td><code>screenWidth</code> <strong>[13]</strong></td></tr><tr><td><code>Device Language</code></td><td><code>context.device.language</code></td><td><code>languageCode</code> <strong>[13]</strong></td></tr><tr><td><code>Device Model</code></td><td><code>context.device.model</code></td><td><code>model</code> <strong>[13]</strong></td></tr><tr><td><code>Device Brand</code></td><td><code>context.device.manufacturer</code></td><td><code>brand</code> <strong>[13]</strong></td></tr><tr><td><code>Merchant Id</code></td><td><code>partners.google.merchant_id</code></td><td><code>merchantId</code> <strong>[15]</strong></td></tr><tr><td><code>Merchant Feed Label</code></td><td><code>partners.google.feed_label</code></td><td><code>merchantFeedLabel</code> <strong>[15]</strong></td></tr><tr><td><code>Merchant Feed Language Code</code></td><td><code>partners.google.feed_language_code</code></td><td><code>merchantFeedLanguageCode</code> <strong>[15]</strong></td></tr><tr><td><code>Transaction Discount</code></td><td><code>discount_value</code></td><td><code>transactionDiscount</code> <strong>[15]</strong></td></tr><tr><td><code>Item List</code></td><td><code>items</code></td><td><code>items</code> <strong>[15]</strong></td></tr><tr><td><code>Item Merchant Product Id</code></td><td><code>items.X.merchant_product_id</code></td><td><code>merchantProductId</code> <strong>[16]</strong></td></tr><tr><td><code>Item Quantity</code></td><td><code>items.X.quantity</code></td><td><code>quantity</code> <strong>[16]</strong></td></tr><tr><td><code>Item Price</code></td><td><code>items.X.product.price</code></td><td><code>unitPrice</code> <strong>[16]</strong></td></tr><tr><td><code>Item Id</code></td><td><code>items.X.id</code></td><td><code>itemId</code> <strong>[16]</strong></td></tr><tr><td><code>Item Merchant Feed Language Code</code></td><td><code>items.X.merchant_feed_lang_code</code></td><td><code>merchantFeedLanguageCode</code> <strong>[16]</strong></td></tr><tr><td><code>Item Original Value</code></td><td><code>items.X.original_value</code></td><td><code>conversionValue</code> <strong>[16]</strong></td></tr><tr><td><code>-</code></td><td><code>Custom Variables</code> (item-level)</td><td><code>customVariables</code> <strong>[16][17]</strong></td></tr><tr><td><code>-</code></td><td><code>Custom Variables</code> (event-level)</td><td><code>customVariables</code> <strong>[3][17]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** Set either the Smart Mapping field `Conversion Action Id` or the `Conversion Action Name` in Mapping. `Conversion Action Id` takes priority. It lets you route each event to a different conversion action.\
**2.** Set in <mark style="color:blue;">`destinations.X`</mark>. `operatingAccount.accountType` is always `GOOGLE_ADS`. Events of the same batch sharing the same conversion action are grouped under a single destination.\
**3.** Set in <mark style="color:blue;">`events.X`</mark>.\
**4.** Only set when your credentials are linked to a manager account (MCC).\
**5.** Expected as a Unix timestamp in milliseconds (number). It's automatically converted to the RFC 3339 format expected by Google. If no value is provided, the processing time is used.\
**6.** Supported values: `WEB`, `APP`, `IN_STORE`, `PHONE`, `MESSAGE` and `OTHER`. Default value: `WEB`.\
**7.** [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) code in uppercase, e.g. `EUR`, `USD`, `JPY`.\
**8.** Set in <mark style="color:blue;">`events.X.userData.userIdentifiers.X`</mark>. See the user identifier requirements at the top of this section.\
**9.** Automatically normalized and hashed (SHA-256) if provided in clear text. Values that are already SHA-256 hashed (64 hexadecimal characters) are sent as is. Emails are trimmed and lowercased; for `gmail.com` and `googlemail.com` addresses, dots and `+` suffixes are also removed from the local part. Phone numbers should be provided in [E.164](https://en.wikipedia.org/wiki/E.164) format, including the leading `+` and country code (e.g. `+33612345678`).\
**10.** Sent in clear text, as required by Google. `User Country` must be an [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) code in uppercase, e.g. `FR`.\
**11.** Supported values: `true` / `false` (Boolean) or `granted` / `denied` (case insensitive). Values are read in the following priority order: 1. the Smart Mapping field, 2. `user.google_consent.ad_user_data` / `user.google_consent.ad_personalization`, 3. `user.google_consent_mode.ad_user_data` / `user.google_consent_mode.ad_personalization`.\
**12.** Set in <mark style="color:blue;">`events.X.adIdentifiers`</mark>. For `gclid`, see Destination setup for the priority order.\
**13.** Set in <mark style="color:blue;">`events.X.eventDeviceInfo`</mark>.\
**14.** Google Ads doesn't support IP address matching for end users in the European Economic Area (EEA), the United Kingdom (UK) or Switzerland (CH). The IP address is automatically excluded only when `User Country` is provided and is one of these countries, as an uppercase ISO 3166-1 alpha-2 code (e.g. `FR`). If `User Country` is missing, the IP address is sent.\
**15.** Set in <mark style="color:blue;">`events.X.cartData`</mark>.\
**16.** Set in <mark style="color:blue;">`events.X.cartData.items.Y`</mark>. Paths are relative to each element of `Item List`.\
**17.** See `Custom Variables` in [Configuration](google-enhanced-conversion.md#configuration).
{% endhint %}

## Google Ads API (legacy)

{% hint style="info" %}
This section applies only when your Google Ads credentials don't include the Data Manager API permission. See Destination setup.\
In this case, events are sent in batches as `ENHANCEMENT` conversion adjustments via [`customers.uploadConversionAdjustments`](https://developers.google.com/google-ads/api/reference/rpc/v24/ConversionAdjustmentUploadService/UploadConversionAdjustments?transport=rest). Settings and fields marked **Data Manager API only** are ignored. The conversion action is always taken from Mapping.
{% endhint %}

{% hint style="warning" %}
**User identifiers (Google Ads API)**\
At least one of the following identifiers must be provided:

* User Email
* User Phone
* User First Name
* User Last Name
* User Street
* User City
* User State
* User Country
* User ZIP Code
{% endhint %}

| Smart Mapping Fields                                                                                       | Commanders Act Default Properties                                                                                                            | Google Properties                                                                           |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `Transaction Id`                                                                                           | `id`                                                                                                                                         | `orderId` **\[\*]**                                                                         |
| `Event Timestamp`                                                                                          | `context.event_timestamp`                                                                                                                    | <p><code>gclidDateTimePair.conversionDateTime</code><br><code>adjustmentDateTime</code></p> |
| `Transaction Value`                                                                                        | `value`                                                                                                                                      | `restatementValue.adjustedValue`                                                            |
| `Currency`                                                                                                 | `currency`                                                                                                                                   | `restatementValue.currencyCode`                                                             |
| `Device User Agent`                                                                                        | `context.device.user_agent`                                                                                                                  | `userAgent`                                                                                 |
| `User Email`                                                                                               | <p><code>user.email</code><br><code>user.email_sha256</code></p>                                                                             | `hashedEmail` **\[1]**                                                                      |
| `User Phone`                                                                                               | `user.phone`                                                                                                                                 | `hashedPhoneNumber` **\[1]**                                                                |
| `User First Name`                                                                                          | `user.firstname`                                                                                                                             | `addressInfo.hashedFirstName` **\[1]**                                                      |
| `User Last Name`                                                                                           | `user.lastname`                                                                                                                              | `addressInfo.hashedLastName` **\[1]**                                                       |
| `User Street`                                                                                              | `user.street`                                                                                                                                | `addressInfo.hashedStreetAddress` **\[1]**                                                  |
| `User City`                                                                                                | `user.city`                                                                                                                                  | `addressInfo.city`                                                                          |
| `User State`                                                                                               | `user.state`                                                                                                                                 | `addressInfo.state`                                                                         |
| `User Country`                                                                                             | `user.country`                                                                                                                               | `addressInfo.countryCode`                                                                   |
| `User ZIP Code`                                                                                            | `user.zipcode`                                                                                                                               | `addressInfo.postalCode`                                                                    |
| <p><code>Google Click Identifier</code><br><code>-</code><br><code>Google Analytics Property Id</code></p> | <p><code>partners.google.gclid</code><br>Cookies <code>_gcl_aw</code>, <code>_gcl_dc</code><br>Cookie <code>_gac_[GA_PROPERTY_ID]</code></p> | `gclidDateTimePair.gclid` **\[2]**                                                          |

{% hint style="info" %}
**\*** Mandatory property.\
**1.** Automatically hashed (SHA-256) if provided in clear text.\
**2.** Only sent when `Event Timestamp` is provided. See Destination setup for the priority order.
{% endhint %}
