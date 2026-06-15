# Amazon Events API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Amazon](https://www.aboutamazon.eu/who-we-are) is a multinational technology company focusing on e-commerce, cloud computing, online advertising, digital streaming, and artificial intelligence. Using this destination you can send conversion data directly to Amazon Ads, bypassing browser-side limitations like ad blockers and cookie restrictions. It complements [Amazon Ad Tag (AAT)](https://advertising.amazon.com/help/GLZ54GXQW773A6MG) to provide more complete attribution across DSP, SD, and STV campaigns, enabling better optimization and lower CPA.

## Key features

The Amazon Events API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [Amazon's event structure](https://advertising.amazon.com/API/docs/en-us/guides/events/events#send-events), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Custom events and properties**: you can freely push custom events and properties based on your specific needs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

{% hint style="warning" %}
If you transmit or make available to Amazon Ads any personal information in connection with your use of any Amazon advertising services in the UK and EEA, you must share a valid consent signal and the country code in which consent was granted by the customer.\
Relevant consent signals include (See [Field mapping](amazon-events-api.md#field-mappings) for more details):\
1\. Amazon Consent (<mark style="color:blue;">`amazonConsent.amznUserData`</mark> and <mark style="color:blue;">`amazonConsent.amznUserData`</mark>`)`\
2\. IAB European Transparency & Consent Framework (`tcf`)\
3\. Global Privacy Policy (`gpp`)\
Amazon Consent fields (1.) are automatically set if you activate our [Amazon Consent Signal integration](https://doc.commandersact.com/features/consent-management/setup-guides/tag-manager/amazon-consent-signal).
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required</code></strong></em><br>Your credentials with Amazon Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>AmazonAds</code></td></tr><tr><td><code>API Base Url</code></td><td><em><strong><code>Required</code></strong></em><br>Your selected Amazon API endpoint. More details are available by following this <a href="https://advertising.amazon.com/API/docs/en-us/reference/api-overview#api-endpoints">LINK</a>.</td></tr><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em><br>Enter your advertiser identifier, as shown in <a href="https://advertising.amazon.com">Amazon Ads</a>, by clicking the <code>gear icon (Administration)</code> in the left-side menu then <code>Account access and settings</code> and <code>Accounts</code>.</td></tr><tr><td><code>Event Source</code></td><td><em><strong><code>Required if not set in Smart Mapping</code></strong></em><br>Select your <code>Event Source</code> from the list or map the <code>Smart Mapping</code> field <code>Event Source</code>.</td></tr><tr><td><code>Country Property</code></td><td><em><strong><code>Required</code></strong></em><br>The property name/path to the country where the event originates from. This value is based on <a href="https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes">ISO 3166-1 alpha-2</a>.</td></tr><tr><td><code>Dataset Name</code></td><td>Dataset name to which this event should be added. Amazon highly recommends to set this field to help organize your conversion definitions. When a dataset name is not provided, a new conversion definitions will be assigned to the <code>default_events</code> dataset. More details are available by following this <a href="https://advertising.amazon.com/API/docs/en-us/guides/events/events#the-datasets-concept">LINK</a>.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Amazon Conversion types and yours events or add new mappings.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Custom data associated with the event. Map your custom event properties by setting their field names in <code>Amazon property name</code> and adding the values in <code>Your value</code> .</td></tr></tbody></table>

## Quick reference

| Commanders Act Events    | Amazon Conversion Types          |
| ------------------------ | -------------------------------- |
| `add_to_cart`            | `ADD_TO_SHOPPING_CART`           |
| `application`            | `APPLICATION`                    |
| `begin_checkout`         | `CHECKOUT`                       |
| `contact`                | `CONTACT`                        |
| `generate_lead`          | `LEAD`                           |
| `purchase`               | `OFF_AMAZON_PURCHASES`           |
| `mobile_app_first_start` | `MOBILE_APP_FIRST_START`         |
| `page_view`              | `PAGE_VIEW`                      |
| `search`                 | `SEARCH`                         |
| `sign_up`                | `SIGN_UP`                        |
| `subscribe`              | `SUBSCRIBE`                      |
| `other`                  | `OTHER`                          |
| `[Any Event]`            | `[Any Conversion Type]` **\[1]** |

{% hint style="info" %}
**1.** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](amazon-events-api.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

{% hint style="warning" %}
At least one identifier must be provided as value for the following "Smart Mapping" fields:\
• `User Email`\
• `User Phone`\
• `First Name`\
• `Last Name`\
• `User Address`\
• `User City`\
• `User State`\
• `User Postal Code`\
• `Device Mobile Identifier`\
• `Ramp Id`\
• `Match Id`\
• `Real Id`\
• `Merkle Id`\
• `Kantar Id`\
See Amazon property <mark style="color:blue;">`matchKeys.X.values.0`</mark> for more details.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="386">Smart Mapping Fields</th><th width="328.6685580062746">Commanders Act Properties</th><th width="311.3314419937253">Amazon Properties</th></tr></thead><tbody><tr><td><p><code>Conversion Type</code></p><p><code>-</code></p></td><td><p><code>partners.amazon.conversion_type</code></p><p><code>(event_name)</code></p></td><td><code>conversionType</code> <strong>[*][1][2]</strong></td></tr><tr><td><p><code>Event Source</code></p><p><code>-</code></p></td><td><p><code>partners.amazon.event_source</code></p><p><code>Event Source</code></p></td><td><code>eventSource</code> <strong>[*][1]</strong></td></tr><tr><td><code>-</code></td><td><code>Country Property</code></td><td><code>countryCode</code> <strong>[*]</strong></td></tr><tr><td><code>-</code></td><td><code>Dataset Name</code></td><td><code>dataSetName</code> <strong>[1][3]</strong></td></tr><tr><td><code>-</code></td><td><code>event_name</code></td><td><code>name</code> <strong>[1]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>eventTime</code></td></tr><tr><td><code>Event Id</code></td><td><code>context.event_id</code></td><td><code>eventId</code> <strong>[4]</strong></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>currencyCode</code></td></tr><tr><td><p><code>User Email</code></p><p><code>User Phone</code></p><p><code>First Name</code></p><p><code>Last Name</code></p><p><code>User Address</code></p><p><code>User City</code></p><p><code>User State</code></p><p><code>User Postal Code</code></p><p><code>Device Mobile Identifier</code></p><p><code>Ramp Id</code></p><p><code>Match Id</code></p><p><code>Real Id</code></p><p><code>Merkle Id</code></p><p><code>Kantar Id</code></p></td><td><p><code>user.email</code></p><p><code>user.phone</code></p><p><code>user.firstname</code></p><p><code>user.lastname</code></p><p><code>user.street</code></p><p><code>user.city</code></p><p><code>user.state</code></p><p><code>user.zipcode</code></p><p><code>context.device.advertising_id</code></p><p><code>partners.amazon.ramp_id</code></p><p><code>partners.amazon.match_id</code></p><p><code>partners.amazon.real_id</code></p><p><code>partners.amazon.merkle_id</code></p><p><code>partners.amazon.kantar_id</code></p></td><td><code>matchKeys.X.values.0</code> <strong>[5]</strong></td></tr><tr><td><p><code>User Email</code></p><p><code>User Phone</code></p><p><code>First Name</code></p><p><code>Last Name</code></p><p><code>User Address</code></p><p><code>User City</code></p><p><code>User State</code></p><p><code>User Postal Code</code></p><p><code>Device Mobile Identifier</code></p><p><code>Ramp Id</code></p><p><code>Match Id</code></p><p><code>Real Id</code></p><p><code>Merkle Id</code></p><p><code>Kantar Id</code></p></td><td><p><code>user.email</code></p><p><code>user.phone</code></p><p><code>user.firstname</code></p><p><code>user.lastname</code></p><p><code>user.street</code></p><p><code>user.city</code></p><p><code>user.state</code></p><p><code>user.zipcode</code></p><p><code>context.device.advertising_id</code></p><p><code>partners.amazon.ramp_id</code></p><p><code>partners.amazon.match_id</code></p><p><code>partners.amazon.real_id</code></p><p><code>partners.amazon.merkle_id</code></p><p><code>partners.amazon.kantar_id</code></p></td><td><code>matchKeys.X.type</code> <strong>[6]</strong></td></tr><tr><td><code>Amazon Consent Ad Storage</code></td><td><code>partners.amazon.ad_storage</code></td><td><code>amazonConsent.amznAdStorage</code> <strong>[7]</strong></td></tr><tr><td><code>Amazon Consent User Data</code></td><td><code>partners.amazon.user_data</code></td><td><code>amazonConsent.amznUserData</code> <strong>[7]</strong></td></tr><tr><td><code>Transparency and Consent Framework String</code></td><td><code>partners.amazon.tcf</code></td><td><code>tcf</code> <strong>[7]</strong></td></tr><tr><td><code>Global Privacy Platform String</code></td><td><code>partners.amazon.gpp</code></td><td><code>gpp</code> <strong>[7]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>ipAddress</code> <strong>[8]</strong></td></tr><tr><td><code>Item List</code></td><td><code>items.length</code></td><td><code>unitsSold</code></td></tr><tr><td><code>Value</code></td><td><code>value</code></td><td><code>value</code></td></tr><tr><td>-</td><td><code>Custom Event Properties</code></td><td><code>customData</code></td></tr><tr><td><code>Limit Data Use</code></td><td><code>partners.amazon.data_processing</code></td><td><code>dataProcessingOptions</code></td></tr><tr><td><code>Ad Event Key</code></td><td><code>partners.amazon.ad_event_key</code></td><td><code>amazonAdEventKey</code></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory field.\
**1.** Set in <mark style="color:blue;">`eventDescription`</mark> .\
**2.** Priority on the left side. See [Quick reference](amazon-events-api.md#quick-reference) for more details.\
**3.** See [Configuration](amazon-events-api.md#configuration) for more details.\
**4.** Your specified id for the conversion event and used for deduplication. More details are available by following this [LINK](https://advertising.amazon.com/API/docs/en-us/guides/events/events#event-de-duplication).\
**5.** At least one identifier must be provided.\
**6.** Depending on the value provided in <mark style="color:blue;">`matchKeys.X.values.0`</mark> , this is one of the following values: <mark style="color:blue;">`EMAIL`</mark> , <mark style="color:blue;">`PHONE`</mark> , <mark style="color:blue;">`FIRST_NAME`</mark> , <mark style="color:blue;">`LAST_NAME`</mark> , <mark style="color:blue;">`ADDRESS`</mark> , <mark style="color:blue;">`CITY`</mark> , <mark style="color:blue;">`STATE`</mark> , <mark style="color:blue;">`POSTAL`</mark> , <mark style="color:blue;">`MAID`</mark> , <mark style="color:blue;">`RAMP_ID`</mark> , <mark style="color:blue;">`MATCH_ID`</mark> , <mark style="color:blue;">`REAL_ID`</mark> , <mark style="color:blue;">`MERKLE_ID`</mark> and <mark style="color:blue;">`KANTAR_ID`</mark> .\
**7.** Set in <mark style="color:blue;">`consent`</mark> . See [Destination setup](amazon-events-api.md#destination-setup) for more details.\
**8.** Set in <mark style="color:blue;">`consent.geo`</mark> .
{% endhint %}
