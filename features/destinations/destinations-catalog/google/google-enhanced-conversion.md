# Google Enhanced Conversions

[Google ](https://about.google/)is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. Taking advantage of the [Google Ads API](https://developers.google.com/google-ads/api/docs/start), you can leverage the [enhanced conversions](https://support.google.com/google-ads/answer/9888656) feature to send first-party data in the form of conversion adjustments. Google uses this additional data to improve the reporting of your online conversions driven by ad interactions.\
The enhanced conversions supplement your existing conversion tags by sending hashed first-party conversion data from your website to Google in a privacy-safe way.

{% hint style="info" %}
You must complete the [setup and configuration steps](https://support.google.com/google-ads/answer/11062876) before you can bridge enhanced conversions via the Google Ads API.
{% endhint %}

## Key features

The Google Enhanced Conversions destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Google method [uploadConversionAdjustments](https://developers.google.com/google-ads/api/rest/reference/rest/v16/customers/uploadConversionAdjustments), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

{% hint style="info" %}
Your user account needs admin rights in the [Google Ads Manager Accounts](https://ads.google.com/intl/en/home/tools/manager-accounts/) where the conversion action is located. When available, this destination will also include the [`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en) value by looking for the following cookies in this priority order:

1. `_gcl_aw`
2. `_gcl_dc`
3. `_gac_[GA_PROPERTY_ID]`
{% endhint %}

### Configuration

<table><thead><tr><th width="357">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with Google Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code></td></tr><tr><td><code>Mapping</code></td><td><p><em><strong><code>Required</code></strong></em> <br>Map your Google Ads conversion names, where enhanced conversions are applied, with your events by setting the fields <code>Google Ads Conversion Name</code> and <code>Your event name</code> . At least one line is required. Conversion names can be found in the Google Ads interface following:</p><p><code>Goals</code> ➜ <code>Summary</code> ➜ <code>Conversion action</code> (column) <strong>[1]</strong><br>If a conversion action is not found the event will be discarded.</p></td></tr><tr><td><code>Google Analytics Property Id</code></td><td>The GA Tracking Id is a string like "UA-XXXXXX-Y" or "G-XXXXXXXXXX" for Google Analytics 4. It's used as an alternative method to retrieve the <a href="https://support.google.com/google-ads/answer/9744275?hl=en"><code>gclid</code></a>  from cookies. See <a href="google-enhanced-conversion.md#destination-setup">Destination setup</a> for more details.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Enhanced conversions must be enabled for your conversion action. This is done in the Google Ads interface following these steps: click on the conversion action ➜ expand `Enhanced conversions` ➜ flag `Turn on enhanced conversions` ➜ select `API` .
{% endhint %}

![Flag "Turn on enhanced conversion" and select "API".](<../../../../.gitbook/assets/2 (1).png>)

## Quick reference

<table><thead><tr><th width="327">Commanders Act Events</th><th>Google Tracking</th></tr></thead><tbody><tr><td><code>[Any Event]</code> <strong>[1]</strong></td><td><code>customers.uploadConversionAdjustments</code></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See [Mapping](google-enhanced-conversion.md#configuration) for more details. &#x20;
{% endhint %}

## Field mappings

{% hint style="warning" %}
At least one of the following identifiers must be provided:

* User email
* User phone
* User first name
* User last name
* User street address
* User city
* User state
* User country
* User zip code
{% endhint %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Google properties are set starting from the path <mark style="color:blue;">`conversionAdjustments.0`</mark>  or  <mark style="color:blue;">`conversionAdjustments.0.userIdentifiers.X`</mark>  with the latter for user properties.
{% endhint %}

<table><thead><tr><th width="334">Commanders Act Properties</th><th>Google Properties</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>orderId</code> <strong>[*]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>userAgent</code></td></tr><tr><td><code>event_timestamp</code></td><td><code>gclidDateTimePair.conversionDateTime</code> <strong>[1]</strong> <br><code>adjustmentDateTime</code> <strong>[1]</strong></td></tr><tr><td><code>value</code></td><td><code>restatementValue.adjustedValue</code></td></tr><tr><td><code>currency</code></td><td><code>restatementValue.currencyCode</code></td></tr><tr><td><p><code>user.email</code></p><p><code>user.email_sha256</code></p></td><td><code>hashedEmail</code> <strong>[2]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>hashedPhoneNumber</code> <strong>[3]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>addressInfo.hashedFirstName</code> <strong>[3]</strong></td></tr><tr><td><code>user.lastname</code></td><td><code>addressInfo.hashedLastName</code> <strong>[3]</strong></td></tr><tr><td><code>user.streetAddress</code></td><td><code>addressInfo.hashedStreetAddress</code> <strong>[3]</strong></td></tr><tr><td><code>user.city</code></td><td><code>addressInfo.city</code></td></tr><tr><td><code>user.state</code></td><td><code>addressInfo.state</code></td></tr><tr><td><code>user.country</code></td><td><code>addressInfo.countryCode</code></td></tr><tr><td><code>user.zipcode</code></td><td><code>addressInfo.postalCode</code></td></tr><tr><td><code>Cookie _gcl_aw</code><br><code>Cookie _gcl_dc</code> <br><code>Cookie _gac_[GA_PROPERTY_ID]</code></td><td><code>gclidDateTimePair.gclid</code> <strong>[4]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** This value is automatically adjusted. See [GclidDateTimePair](https://developers.google.com/google-ads/api/rest/reference/rest/v11/customers/uploadConversionAdjustments#gcliddatetimepair) for more details.\
**\[2]** If <mark style="color:blue;">`user.email`</mark> is provided, it's hashed using SHA256, otherwise , <mark style="color:blue;">`user.email_sha256`</mark> is used.\
**\[3]** Normalized and hashed via SHA256.\
**\[4]** See [Destination setup](google-enhanced-conversion.md#destination-setup) for more details.
{% endhint %}
