# Google Conversion Adjustments

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Google](https://about.google/) is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. Taking advantage of the [Google Ads API Upload Conversion Adjustments](https://developers.google.com/google-ads/api/docs/conversions/upload-adjustments), you can amend conversions values initially reported by other means (E.g. via client-side tags).

## Destination setup

To adjust a conversion, you must first have a conversion action [set up](https://support.google.com/google-ads/answer/1722054), and conversions must have been reported in Google Ads interface.

{% hint style="info" %}
Google recommends waiting 24 hours after a conversion is reported before sending adjustments. This will avoid[`CONVERSION_NOT_FOUND`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionAdjustmentUploadErrorEnum.ConversionAdjustmentUploadError#conversion\_not\_found)or[`TOO_RECENT_CONVERSION`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionAdjustmentUploadErrorEnum.ConversionAdjustmentUploadError#too\_recent\_conversion) upload errors. Also, wait 4-6 hours after creating a [conversion action](https://support.google.com/google-ads/answer/6032150?sjid=6242609434917944234-EU) before adjusting its conversions to avoid a[`TOO_RECENT_CONVERSION_ACTION`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionAdjustmentUploadErrorEnum.ConversionAdjustmentUploadError#too\_recent\_conversion\_action)upload error.
{% endhint %}

{% hint style="info" %}
To identify the conversion and when a transaction identifier is not provided, this destination will try to include the[`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en)if its value is provided in the <mark style="color:blue;">`Google Click Id`</mark> field (See [Configuration](google-conversion-adjustments.md#configuration) for more details). If this is not set, the following cookies, in the presented priority order, are used to retrieve a proper value:

1. `_gcl_aw`
2. `_gcl_dc`
3. `_gac_[GA_PROPERTY_ID]`

On the other hand, when a transaction identifier is present both the[`gclid`](https://support.google.com/google-ads/answer/9744275?hl=en)and<mark style="color:blue;">`conversionDateTime`</mark>are removed from the hit to prevent the [`GCLID_DATE_TIME_PAIR_AND_ORDER_ID_BOTH_SET`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionAdjustmentUploadErrorEnum.ConversionAdjustmentUploadError#gclid\_date\_time\_pair\_and\_order\_id\_both\_set)upload error. More details on all upload errors are available following this [LINK](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionAdjustmentUploadErrorEnum.ConversionAdjustmentUploadError).
{% endhint %}

{% hint style="warning" %}
Conversion adjustments don't work with [conversion actions](https://support.google.com/google-ads/answer/6032150?sjid=6242609434917944234-EU) whose type is[`UNKNOWN`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionActionTypeEnum.ConversionActionType#unknown). In addition, adjustments for a conversion whose click has a<mark style="color:blue;">`gbraid`</mark>or<mark style="color:blue;">`wbraid`</mark>instead of a[`gclid`](https://support.google.com/google-ads/answer/1033981)will fail with a[`CONVERSION_NOT_FOUND`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionAdjustmentUploadErrorEnum.ConversionAdjustmentUploadError#conversion\_not\_found)upload error.
{% endhint %}

### Configuration

<table><thead><tr><th width="325">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your credentials with Google Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code></p></td></tr><tr><td><code>Mapping</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Map your Google Ads Conversion Name(s), where conversion value adjustments are applied, with Commanders Act event(s) by setting your <code>Google Ads Conversion Name</code><br>and <code>Your event name</code>. At least one line is required. Conversion names can be found in the Google Ads interface following:</p><p><code>TOOLS &#x26; SETTINGS</code> ➜ <code>Measurement</code> ➜ <code>Conversions</code> ➜ <code>Conversion action</code>.<br>If a conversion action is not found the event will be discarded.</p></td></tr><tr><td><code>Google Click Id</code></td><td>Google click Id (gclid) associated with the original conversion. This field has priority over related cookies.</td></tr><tr><td><code>Google Analytics Property Id</code></td><td>The GA Tracking Id is a string like "UA-XXXXXX-Y" or "G-XXXXXXXXXX" for Google Analytics 4. It's used as an alternative method to retrieve the <a href="https://support.google.com/google-ads/answer/9744275?hl=en"><code>gclid</code></a> from cookies. See <a href="google-conversion-adjustments.md#destination-setup">Destination setup</a> for more details.</td></tr></tbody></table>

## Field mappings

{% hint style="info" %}
The transaction identifier (id) is required in any of the following conditions:

1. The type of the [conversion action](https://support.google.com/google-ads/answer/6032150?sjid=6242609434917944234-EU) is equal to <mark style="color:blue;">`Website /`</mark>[`WEBPAGE`](https://developers.google.com/google-ads/api/reference/rpc/v14/ConversionActionTypeEnum.ConversionActionType#webpage).
2. The original conversion you are adjusting was assigned a transaction identifier.

If<mark style="color:blue;">`Transaction Adjusted Timestamp (adjustmentDateTime)`</mark>"Smart Mapping" field is not set, this destination will use the current timestamp to set the Google property <mark style="color:blue;">`conversionAdjustments.0.adjustmentDateTime`</mark>.
{% endhint %}

<table><thead><tr><th width="326">Commanders Act Properties</th><th>Google Conversion Adjustments Properties</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>conversionAdjustments.0.restatementValue.adjustedValue</code> <strong>[*]</strong></td></tr><tr><td><code>id</code></td><td><code>conversionAdjustments.0.orderId</code> <strong>[1]</strong></td></tr><tr><td><code>currency</code></td><td><code>conversionAdjustments.0.restatementValue.currencyCode</code></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>conversionAdjustments.0.gclidDateTimePair.conversionDateTime</code></td></tr><tr><td><p><code>Google Click Id</code></p><p><code>Cookie _gcl_aw</code><br><code>Cookie _gcl_dc</code><br><code>Cookie _gac_[GA_PROPERTY_ID]</code></p></td><td><code>conversionAdjustments.0.gclidDateTimePair.gclid</code> <strong>[2]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** This is required when specific conditions are verified. See [Field mappings](google-conversion-adjustments.md#field-mappings) for details.\
**\[2]** See [Destination setup](google-conversion-adjustments.md#destination-setup) for more details.
{% endhint %}
