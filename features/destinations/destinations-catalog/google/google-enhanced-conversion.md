# Google Enhanced Conversions

[Google ](https://about.google/)is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. Taking advantage of the [Google Ads API](https://developers.google.com/google-ads/api/docs/start), you can leverage the [enhanced conversions](https://support.google.com/google-ads/answer/9888656) feature to send first-party data in the form of conversion adjustments. Google uses this additional data to improve the reporting of your online conversions driven by ad interactions.\
The enhanced conversions supplement your existing conversion tags by sending hashed first-party conversion data from your website to Google in a privacy-safe way.

{% hint style="info" %}
You must complete the [setup and configuration steps](https://support.google.com/google-ads/answer/11062876) before you can bridge enhanced conversions via the Google Ads API.
{% endhint %}

## Destination setup

{% hint style="info" %}
Your user account needs admin rights in the [Google Ads Manager Accounts](https://ads.google.com/intl/en/home/tools/manager-accounts/) where the conversion action is located. When available, this destination will also include the[`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en)value by looking for the following cookies in this priority order:

1. `_gcl_aw`
2. `_gcl_dc`
3. `_gac_[GA_PROPERTY_ID]`
{% endhint %}

### Configuration

| Settings                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Authentication`               | <p><em><strong><code>Required</code></strong></em></p><p>Your credentials with Google Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code></p>                                                                                                                                                                                                                                                                                                                 |
| `Mapping`                      | <p><em><strong><code>Required</code></strong></em></p><p>Map your Google Ads Conversion Name(s), where enhanced conversions are applied, with Commanders Act event(s) by setting your <code>Google Ads Conversion Name</code><br>and <code>Your event name</code>. At least one line is required. Conversion names can be found in the Google Ads interface following:</p><p><code>TOOLS &#x26; SETTINGS</code> ➜ <code>Measurement</code> ➜ <code>Conversions</code> ➜ <code>Conversion action</code> <strong>[1]</strong><br>If a conversion action is not found the event will be discarded.</p> |
| `Google Analytics Property Id` | The GA Tracking Id is a string like "UA-XXXXXX-Y" or "G-XXXXXXXXXX" for Google Analytics 4. It's used as an alternative method to retrieve the [`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en) from cookies. See [Destination setup](google-enhanced-conversion.md#destination-setup) for more details.                                                                                                                                                                                                                                                                       |

{% hint style="info" %}
**\[1]** Enhanced conversions must be enabled for your conversion action. This is done in the Google Ads interface following these steps: click on the conversion action ➜ expand `Enhanced conversions`➜ flag `Turn on enhanced conversions`➜ select `API`.
{% endhint %}

![Flag "Turn on enhanced conversion" and select "API".](<../../../../.gitbook/assets/2 (1).png>)

## Quick reference

<table><thead><tr><th width="327">Commanders Act Events</th><th>Google Tracking</th></tr></thead><tbody><tr><td><code>[Any Event]</code> <strong>[1]</strong></td><td><code>customers.uploadConversionAdjustments</code></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See [Mapping](google-enhanced-conversion.md#configuration) for more details. &#x20;
{% endhint %}

## Field mappings

{% hint style="info" %}
**At least** one of the following user identifiers must be set:

* <mark style="color:blue;">`user.email`</mark>or<mark style="color:blue;">`user.email_sha256`</mark>
* <mark style="color:blue;">`user.phone`</mark>
* <mark style="color:blue;">`user.firstname`</mark>
* <mark style="color:blue;">`user.lastname`</mark>
* <mark style="color:blue;">`user.streetAddress`</mark>
* <mark style="color:blue;">`user.city`</mark>
* <mark style="color:blue;">`user.state`</mark>
* <mark style="color:blue;">`user.country`</mark>
* <mark style="color:blue;">`user.zipcode`</mark>

This will prevent the error<mark style="color:blue;">`incomplete_any_user_identifier_is_required`</mark>to be raised.
{% endhint %}

| Commanders Act Properties                                                                                      | Google Enhanced Conversions Properties                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                           | `conversionAdjustments.X.orderId` **\[\*]**                                                                                                                                               |
| `context.device.user_agent`                                                                                    | `conversionAdjustments.X.userAgent`                                                                                                                                                       |
| `event_timestamp`                                                                                              | <p><code>conversionAdjustments.X.gclidDateTimePair.conversionDateTime</code> <strong>[1]</strong> and<br><code>conversionAdjustments.X.adjustmentDateTime</code> <strong>[1]</strong></p> |
| `value`                                                                                                        | `conversionAdjustments.X.restatementValue.adjustedValue`                                                                                                                                  |
| `currency`                                                                                                     | `conversionAdjustments.X.restatementValue.currencyCode`                                                                                                                                   |
| <p><code>user.email</code></p><p><code>user.email_sha256</code></p>                                            | `conversionAdjustments.X.userIdentifiers.Y.hashedEmail` **\[2]**                                                                                                                          |
| `user.phone`                                                                                                   | `conversionAdjustments.X.userIdentifiers.Y.hashedPhoneNumber` **\[3]**                                                                                                                    |
| `user.firstname`                                                                                               | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedFirstName` **\[3]**                                                                                                          |
| `user.lastname`                                                                                                | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedLastName` **\[3]**                                                                                                           |
| `user.streetAddress`                                                                                           | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedStreetAddress` **\[3]**                                                                                                      |
| `user.city`                                                                                                    | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.city`                                                                                                                              |
| `user.state`                                                                                                   | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.state`                                                                                                                             |
| `user.country`                                                                                                 | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.countryCode`                                                                                                                       |
| `user.zipcode`                                                                                                 | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.postalCode`                                                                                                                        |
| <p><code>Cookie _gcl_aw</code><br><code>Cookie _gcl_dc</code><br><code>Cookie _gac_[GA_PROPERTY_ID]</code></p> | `conversionAdjustments.X.gclidDateTimePair.gclid` **\[4]**                                                                                                                                |

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** This value is automatically adjusted. See [GclidDateTimePair](https://developers.google.com/google-ads/api/rest/reference/rest/v11/customers/uploadConversionAdjustments#gcliddatetimepair) for more details.\
**\[2]** If<mark style="color:blue;">`user.email`</mark>is provided, it's hashed using SHA256, otherwise , <mark style="color:blue;">`user.email_sha256`</mark>is used.\
**\[3]** Normalized and hashed via SHA256.\
**\[4]** See [Destination setup](google-enhanced-conversion.md#destination-setup) for more details.
{% endhint %}
