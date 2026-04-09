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
• Amazon Consent (`amazonConsent.amznUserData` and `amazonConsent.amznUserData)`\
• IAB European Transparency & Consent Framework (`tcf`)\
• Global Privacy Policy (`gpp`)\
Amazon Consent fields are automatically set if you activate our [Amazon Consent Signal integration](https://doc.commandersact.com/features/consent-management/setup-guides/tag-manager/amazon-consent-signal).
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required</code></strong></em><br>Your credentials with Amazon Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>AmazonAds</code></td></tr><tr><td><code>API Base Url</code></td><td><em><strong><code>Required</code></strong></em><br>Your selected Amazon API endpoint. More details are available by following this <a href="https://advertising.amazon.com/API/docs/en-us/reference/api-overview#api-endpoints">LINK</a>.</td></tr><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em><br>Enter your advertiser identifier, as shown in <a href="https://advertising.amazon.com">Amazon Ads</a>, by clicking the <code>gear icon (Administration)</code> in the left-side menu then <code>Account access and settings</code> and <code>Accounts</code>.</td></tr><tr><td><code>Conversion Type</code></td><td><em><strong><code>Required if not set in Smart Mapping</code></strong></em><br>Select your <code>Conversion Type</code> from the list or map the <code>Smart Mapping</code> field <code>Conversion Type</code>.</td></tr><tr><td><code>Event Source</code></td><td><em><strong><code>Required if not set in Smart Mapping</code></strong></em><br>Select your <code>Event Source</code> from the list or map the <code>Smart Mapping</code> field <code>Event Source</code>.</td></tr><tr><td><code>Country Property</code></td><td><em><strong><code>Required</code></strong></em><br>The property name/path to the country where the event originates from. This value is based on <a href="https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes">ISO 3166-1 alpha-2</a>.</td></tr><tr><td><code>Dataset Name</code></td><td>Dataset name to which this event should be added. Amazon highly recommends to set this field  to help organize your conversion definitions. When a dataset name is not provided, a new conversion definitions will be assigned to the <code>default_events</code> dataset. More details are available by following this <a href="https://advertising.amazon.com/API/docs/en-us/guides/events/events#the-datasets-concept">LINK</a>.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Custom data associated with the event. Map your custom event properties by setting their field names in <code>Amazon property name</code> and adding the values in <code>Your value</code> .</td></tr></tbody></table>

## Quick reference

<table><thead><tr><th width="336">Commanders Act Events</th><th>Amazon Event</th></tr></thead><tbody><tr><td><code>[Any Event]</code> <strong>[1]</strong></td><td><code>[Any Event]</code></td></tr></tbody></table>

{% hint style="info" %}
> **\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="359.6685580062746">Commanders Act Properties</th><th>Amazon Properties</th></tr></thead><tbody><tr><td><code>partners.amazon.conversion_type</code><br><code>Conversion Type</code></td><td><code>conversionType</code> <strong>[*][1][2]</strong></td></tr><tr><td><code>Event Source</code></td><td><code>eventSource</code> <strong>[*][1]</strong></td></tr><tr><td><code>Country Property</code></td><td><code>countryCode</code> <strong>[*]</strong></td></tr><tr><td><code>Dataset Name</code></td><td><code>dataSetName</code> <strong>[1][3]</strong></td></tr><tr><td><code>event_name</code></td><td><code>name</code> <strong>[1]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>eventTime</code></td></tr><tr><td><code>context.event_id</code></td><td><code>eventId</code> <strong>[4]</strong></td></tr><tr><td><code>currency</code></td><td><code>currencyCode</code></td></tr><tr><td><p><code>user.email</code><br><code>user.phone</code></p><p><code>user.firstname</code></p><p><code>user.lastname</code></p><p><code>user.street</code></p><p><code>user.city</code> <br><code>user.state</code> <br><code>user.zipcode</code> <br><code>context.device.advertising_id</code> <br><code>partners.amazon.ramp_id</code> <br><code>partners.amazon.match_id</code></p><p><code>partners.amazon.real_id</code> <br><code>partners.amazon.merkle_id</code></p><p><code>partners.amazon.kantar_id</code></p></td><td><code>matchKeys.X.values.0</code> <strong>[5]</strong></td></tr><tr><td><p><code>(user.email</code><br><code>user.phone</code></p><p><code>user.firstname</code></p><p><code>user.lastname</code></p><p><code>user.street</code></p><p><code>user.city</code> <br><code>user.state</code> <br><code>user.zipcode</code> <br><code>context.device.advertising_id</code> <br><code>partners.amazon.ramp_id</code> <br><code>partners.amazon.match_id</code></p><p><code>partners.amazon.real_id</code> <br><code>partners.amazon.merkle_id</code></p><p><code>partners.amazon.kantar_id)</code></p></td><td><code>matchKeys.X.type</code> <strong>[6]</strong></td></tr><tr><td><code>partners.amazon.ad_storage</code></td><td><code>amazonConsent.amznAdStorage</code> <strong>[7]</strong></td></tr><tr><td><code>partners.amazon.user_data</code></td><td><code>amazonConsent.amznUserData</code> <strong>[7]</strong></td></tr><tr><td><code>partners.amazon.tcf</code></td><td><code>tcf</code> <strong>[7]</strong></td></tr><tr><td><code>partners.amazon.gpp</code></td><td><code>gpp</code> <strong>[7]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>ipAddress</code> <strong>[8]</strong></td></tr><tr><td><code>items.length</code></td><td><code>unitsSold</code></td></tr><tr><td><code>value</code></td><td><code>value</code></td></tr><tr><td><code>Custom Event Properties</code></td><td><code>customData</code></td></tr><tr><td><code>partners.amazon.data_processing</code></td><td><code>dataProcessingOptions</code></td></tr><tr><td><code>partners.amazon.ad_event_key</code></td><td><code>amazonAdEventKey</code></td></tr></tbody></table>

{% hint style="info" %}
> **\[\*]** Mandatory field.\
> **\[1]** Set in <mark style="color:blue;">`eventDescription`</mark> .\
> &#xNAN;**\[2]** Priority on the left side.\
> &#xNAN;**\[3]** See [Configuration](amazon-events-api.md#configuration) for more details.\
> &#xNAN;**\[4]** Your specified id for the conversion event and used for deduplication. More details are available by following this [LINK](https://advertising.amazon.com/API/docs/en-us/guides/events/events#event-de-duplication).\
> &#xNAN;**\[5]** At least one identifier must be provided.\
> &#xNAN;**\[6]** Depending on the value provided in `matchKeys.X.values.0` , this is one of the following values: `EMAIL` , `PHONE` , `FIRST_NAME` , `LAST_NAME` , `ADDRESS` , `CITY` , `STATE` , `POSTAL` , `MAID` , `RAMP_ID` , `MATCH_ID` , `REAL_ID` , `MERKLE_ID`  and `KANTAR_ID` .\
> **\[7]** Set in <mark style="color:blue;">`consent`</mark> . See [Destination setup](amazon-events-api.md#destination-setup) for more details.\
> &#xNAN;**\[8]** Set in <mark style="color:blue;">`consent.geo`</mark> .
{% endhint %}
