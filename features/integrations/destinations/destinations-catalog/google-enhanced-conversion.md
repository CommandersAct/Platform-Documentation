# Google Enhanced Conversions

Taking advantage of the [Google Ads API](https://developers.google.com/google-ads/api/docs/start), you can use the [enhanced conversions](https://support.google.com/google-ads/answer/9888656) feature to send first-party customer data in the form of conversion adjustments. Google uses this additional data to improve the reporting of your online conversions driven by ad interactions.\
The enhanced conversions supplements your existing conversion tags by sending hashed first party conversion data from your website to Google in a privacy safe way.

{% hint style="info" %}
You must complete the [setup and configuration steps](https://support.google.com/google-ads/answer/11062876) before you can bridge enhanced conversions via the Google Ads API.
{% endhint %}

## Destination setup

{% hint style="info" %}
Your user account needs admin rights in the [Google Ads Manager Accounts](https://ads.google.com/intl/en/home/tools/manager-accounts/) where the conversion action is located - It's required for this destination to work.
{% endhint %}

### Configuration

| Settings                     | Description                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Authentication               | <p><em><strong><code>Required</code></strong></em></p><p>Your credentials with Google Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code></p>                                                                                                                              |
| Conversion Action            | <p><em><strong><code>Required</code></strong></em></p><p>Your conversion action name where enhanced conversions are applied. This is found in the Google Ads interface following:</p><p><code>TOOLS &#x26; SETTINGS</code> ➜ <code>Measurement</code> ➜ <code>Conversions</code> ➜ <code>Conversion action</code> <strong>[1]</strong><br>If the conversion action is not found the event will be discarded.</p> |
| Google Analytics Property Id | <p><em><strong><code>Required</code></strong></em><br>The GA Tracking ID is a string like "UA-XXXXXX-Y". It's used to retrieve your <a href="https://support.google.com/google-ads/answer/9744275?hl=en"><code>gclid</code></a> from cookie(s).</p>                                                                                                                                                              |

{% hint style="info" %}
**\[1]** Enhanced conversions must be enabled for your conversion action. This is done in the Google Ads interface following these steps: click on the conversion action ➜ expand `Enhanced conversions`➜ flag `Turn on enhanced conversions`➜ select `API`.
{% endhint %}

![Click on your "Conversion Action" (E.g. "Purchase")](<../../../../.gitbook/assets/capture-de-cran-2020-10-29-a-10.30.43 (1).png>)

![Flag "Turn on enhanced conversion" and select "API".](<../../../../.gitbook/assets/1 (2).png>)

## Field mappings

| Commanders Act Properties                                 | Google Enhanced Conversions Properties                                                                                                                                                    |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `device.user_agent`                                       | `conversionAdjustments.X.userAgent`                                                                                                                                                       |
| `properties.id`                                           | `conversionAdjustments.X.orderId`                                                                                                                                                         |
| `event_timestamp`                                         | <p><code>conversionAdjustments.X.gclidDateTimePair.conversionDateTime</code> <strong>[1]</strong> and<br><code>conversionAdjustments.X.adjustmentDateTime</code> <strong>[1]</strong></p> |
| `properties.value`                                        | `conversionAdjustments.X.restatementValue.adjustedValue`                                                                                                                                  |
| `properties.currency`                                     | `conversionAdjustments.X.restatementValue.currencyCode`                                                                                                                                   |
| `properties.user.email` or `properties.user.email_sha256` | `conversionAdjustments.X.userIdentifiers.Y.hashedEmail` **\[2]**                                                                                                                          |
| `properties.user.phone`                                   | `conversionAdjustments.X.userIdentifiers.Y.hashedPhoneNumber` **\[3]**                                                                                                                    |
| `properties.user.firstname`                               | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedFirstName` **\[3]**                                                                                                          |
| `properties.user.lastname`                                | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedLastName` **\[3]**                                                                                                           |
| `properties.user.streetAddress`                           | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.hashedStreetAddress` **\[3]**                                                                                                      |
| `properties.user.city`                                    | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.city` \*\*\*\*                                                                                                                     |
| `properties.user.state`                                   | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.state`                                                                                                                             |
| `properties.user.country`                                 | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.countryCode`                                                                                                                       |
| `properties.user.zipcode`                                 | `conversionAdjustments.X.userIdentifiers.Y.addressInfo.postalCode`                                                                                                                        |

{% hint style="info" %}
**\[1]** This value is automatically adjusted. See [GclidDateTimePair](https://developers.google.com/google-ads/api/rest/reference/rest/v11/customers/uploadConversionAdjustments#gcliddatetimepair) for more details.\
**\[2]** If<mark style="color:blue;">`properties.user.email`</mark> is provided, it's hashed using`SHA-256`, otherwise, <mark style="color:blue;">`properties.user.email_sha256`</mark>is used.\
**\[3]** Normalized and hashed using `SHA-256`.
{% endhint %}
