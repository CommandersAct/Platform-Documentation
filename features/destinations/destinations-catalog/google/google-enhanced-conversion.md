# Google Enhanced Conversions

[Google ](https://about.google/)is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. Taking advantage of the [Google Ads API](https://developers.google.com/google-ads/api/docs/start), you can leverage the [enhanced conversions](https://support.google.com/google-ads/answer/9888656) feature to send first-party data in the form of conversion adjustments. Google uses this additional data to improve the reporting of your online conversions driven by ad interactions.\
The enhanced conversions supplement your existing conversion tags by sending hashed first-party conversion data from your website to Google in a privacy-safe way.

{% hint style="info" %}
You must complete the [setup and configuration steps](https://support.google.com/google-ads/answer/11062876) before you can bridge enhanced conversions via the Google Ads API.
{% endhint %}

## Destination setup

{% hint style="info" %}
Your user account needs admin rights in the [Google Ads Manager Accounts](https://ads.google.com/intl/en/home/tools/manager-accounts/) where the conversion action is located.
{% endhint %}

### Configuration

| Settings                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Authentication`               | <p><em><strong><code>Required</code></strong></em></p><p>Your credentials with Google Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code></p>                                                                                                                                                                                                                                                                                                                               |
| `Mapping`                      | <p><em><strong><code>Required</code></strong></em></p><p>Map your Google Ads Conversion Name(s), where enhanced conversions are applied, with Commanders Act event(s) by setting at least a <code>Google Ads Conversion Name</code><br>and a field <code>Your event name</code>. At least one line is required. Conversion names can be found in the Google Ads interface following:</p><p><code>TOOLS &#x26; SETTINGS</code> ➜ <code>Measurement</code> ➜ <code>Conversions</code> ➜ <code>Conversion action</code> <strong>[1]</strong><br>If a conversion action is not found the event will be discarded.</p> |
| `Google Analytics Property Id` | The GA Tracking ID is a string like "UA-XXXXXX-Y". It's used to retrieve your [`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en) from cookie(s).                                                                                                                                                                                                                                                                                                                                                                                                                                               |

{% hint style="info" %}
**\[1]** Enhanced conversions must be enabled for your conversion action. This is done in the Google Ads interface following these steps: click on the conversion action ➜ expand `Enhanced conversions`➜ flag `Turn on enhanced conversions`➜ select `API`.
{% endhint %}

![Flag "Turn on enhanced conversion" and select "API".](<../../../../.gitbook/assets/2 (1).png>)

## Field mappings

| Commanders Act Properties                                 | Google Enhanced Conversions Properties                                                                                                                                                    |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `properties.id`                                           | `conversionAdjustments.X.orderId` **\[\*]**                                                                                                                                               |
| `device.user_agent`                                       | `conversionAdjustments.X.userAgent`                                                                                                                                                       |
| `event_timestamp`                                         | <p><code>conversionAdjustments.X.gclidDateTimePair.conversionDateTime</code> <strong>[1]</strong> and<br><code>conversionAdjustments.X.adjustmentDateTime</code> <strong>[1]</strong></p> |
| `properties.value`                                        | `conversionAdjustments.X.restatementValue.adjustedValue`                                                                                                                                  |
| `properties.currency`                                     | `conversionAdjustments.X.restatementValue.currencyCode`                                                                                                                                   |
| `properties.user.email` or `properties.user.email_sha256` | `conversionAdjustments.X.userIdentifiers.Y.hashedEmail` **\[2]**                                                                                                                          |
| `properties.user.phone`                                   | `conversionAdjustments.X.userIdentifiers.Y.hashedPhoneNumber` **\[3]**                                                                                                                    |
| `properties.user.firstname`                               | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedFirstName` **\[3]**                                                                                                          |
| `properties.user.lastname`                                | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedLastName` **\[3]**                                                                                                           |
| `properties.user.streetAddress`                           | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedStreetAddress` **\[3]**                                                                                                      |
| `properties.user.city`                                    | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.city`                                                                                                                              |
| `properties.user.state`                                   | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.state`                                                                                                                             |
| `properties.user.country`                                 | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.countryCode`                                                                                                                       |
| `properties.user.zipcode`                                 | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.postalCode`                                                                                                                        |

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** This value is automatically adjusted. See [GclidDateTimePair](https://developers.google.com/google-ads/api/rest/reference/rest/v11/customers/uploadConversionAdjustments#gcliddatetimepair) for more details.\
**\[2]** If<mark style="color:blue;">`properties.user.email`</mark>is provided, it's hashed using`SHA-256`, otherwise, <mark style="color:blue;">`properties.user.email_sha256`</mark>is used.\
**\[3]** Normalized and hashed via SHA256.
{% endhint %}
