# Amazon Ads Conversions API

[Amazon](https://www.aboutamazon.eu/who-we-are) is a multinational technology company focusing on e-commerce, cloud computing, online advertising, digital streaming, and artificial intelligence.\
Using this destination you can import conversion event data in [Amazon DSP](https://advertising.amazon.com/solutions/products/amazon-dsp).

## Key features

The Amazon Ads Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [Amazon's conversion definitions/types](https://advertising.amazon.com/API/docs/en-us/dsp-conversion-builder#tag/Amazon-Conversion-Definitions/operation/dspAmazonCreateConversionDefinitions), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;

## Destination setup

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with Amazon Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>AmazonAds</code></td></tr><tr><td><code>API Base Url</code></td><td><em><strong><code>Required</code></strong></em>  <br>Your selected Amazon API endpoint. More details are available by following this <a href="https://advertising.amazon.com/API/docs/en-us/reference/api-overview#api-endpoints">LINK</a>.</td></tr><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Your account identifier you use to access the DSP. This is your DSP Advertiser ID. DSP Entity ID is not supported.</td></tr><tr><td><code>Profile Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Select your profile identifier.</td></tr><tr><td><code>Conversion Definition Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Select your conversion definition identifier.</td></tr><tr><td><code>Country</code></td><td><em><strong><code>Required</code></strong></em> <br>The country where the event originates from. E.g. "US". This value is based on <a href="https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes">ISO 3166-1 alpha-2</a>.</td></tr></tbody></table>

## Quick reference

<table><thead><tr><th width="336">Commanders Act Events</th><th>Amazon Tracking</th></tr></thead><tbody><tr><td><code>[Any Event]</code> <strong>[1]</strong></td><td><code>[Any Conversion Definitions/Types]</code> <strong>[2]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.\
&#xNAN;**\[2] See** <mark style="color:blue;">`Conversion Definition Id`</mark> in [Configuration](amazon-ads-conversions-api.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All Amazon properties are include in <mark style="color:blue;">`eventData.0`</mark> .
{% endhint %}

{% hint style="warning" %}
At least one identifier must be provided in <mark style="color:blue;">`matchKeys`</mark> .
{% endhint %}

<table><thead><tr><th width="359.6685580062746">Commanders Act Properties</th><th>Amazon Properties</th></tr></thead><tbody><tr><td><code>Country</code></td><td><code>countryCode</code> <strong>[*]</strong></td></tr><tr><td><code>event_name</code></td><td><code>name</code> <strong>[*]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>timestamp</code> <strong>[*]</strong></td></tr><tr><td><code>Conversion Definition Id</code></td><td><code>conversionDefinitionId</code> <strong>[*]</strong></td></tr><tr><td><p><code>user.email_sha256</code></p><p><code>user.phone</code></p><p><code>user.firstname</code></p><p><code>user.lastname</code></p><p><code>user.street</code></p><p><code>user.city</code></p><p><code>user.state</code></p><p><code>user.zipcode</code></p><p><code>context.device.advertising_id</code></p></td><td><code>matchKeys.X.values[0]</code> <strong>[1]</strong></td></tr><tr><td><p><code>(user.email_sha256</code></p><p><code>user.phone</code></p><p><code>user.firstname</code></p><p><code>user.lastname</code></p><p><code>user.street</code></p><p><code>user.city</code></p><p><code>user.state</code></p><p><code>user.zipcode</code></p><p><code>context.device.advertising_id)</code></p></td><td><code>matchKeys.X.type</code> <strong>[2]</strong></td></tr><tr><td><code>items.length</code></td><td><code>unitsSold</code></td></tr><tr><td><code>value</code></td><td><code>value</code></td></tr><tr><td><code>currency</code></td><td><code>currencyCode</code></td></tr><tr><td><code>context.event_id</code></td><td><code>clientDedupeId</code> <strong>[3]</strong></td></tr><tr><td><code>partners.amazon.data_processing</code></td><td><code>dataProcessingOptions</code> <strong>[4]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
&#xNAN;**\[1]** At least one identifier must be provided.\
&#xNAN;**\[2]** Depending on the value provided in <mark style="color:blue;">`matchKeys.X.values[0]`</mark> , this is one of the following values: <mark style="color:blue;">`EMAIL`</mark>, <mark style="color:blue;">`PHONE`</mark>, <mark style="color:blue;">`FIRST_NAME`</mark>, <mark style="color:blue;">`LAST_NAME`</mark>, <mark style="color:blue;">`ADDRESS`</mark>, <mark style="color:blue;">`CITY`</mark>, <mark style="color:blue;">`STATE`</mark>, <mark style="color:blue;">`POSTAL`</mark> or <mark style="color:blue;">`MAID`</mark>.\
&#xNAN;**\[3]** The client specified id for the conversion event. For events with the same <mark style="color:blue;">`clientDedupeId`</mark> only the latest event will be kept.\
&#xNAN;**\[4]** This is set with with <mark style="color:blue;">`LIMITED_DATA_USE`</mark> when <mark style="color:blue;">`partners.amazon.data_processing`</mark> is a non-empty string, non-false (boolean), non-zero (number) value.
{% endhint %}
