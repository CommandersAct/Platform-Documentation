# Google Enhanced Conversions for Leads

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Google](https://about.google/) is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. This destination let you improve the accuracy of your offline conversion measurement by uploading click conversions that contain hashed user identifiers and some optional additional details that help Google Ads match the conversion to the ad that initiated the lead.

## Key features

The Google Enhanced Conversions for Leads destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Google method [uploadClickConversions](https://developers.google.com/google-ads/api/rest/reference/rest/v17/customers/uploadClickConversions?hl=en#ClickConversion), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to the partner.

## Destination setup

Before configuring this destination, you need to fullfil the following Google prerequisites:

{% hint style="info" %}
### 1.  Create and configure your conversion action

Login into [Google Ads ](https://ads.google.com/home/)and:

* Click **Goals**
* Click the **Conversion** drop down in the menu section.
* Click [**Summary**](https://ads.google.com/aw/conversions)
* Click **New conversion action**.
* Select **Import** in the "New conversion action” page.
* Select **CRMs, files, or other data sources** and then **Track conversions from clicks**.
* In the “Data Source” section, you can select **Connect a new data source**: this can be done at a later stage.
* Click **Continue**.
* Enter the settings for this conversion action. For details on the settings, check out [Set up offline conversion imports](https://support.google.com/google-ads/answer/7012522?sjid=17218141641119059045-EU).
* Click **Save and continue**. The next page will confirm your new conversion action.
* Click **Done**.\


### 2. Turn on enhanced conversions for leads

Check the box to turn on enhanced conversions for leads or you can do it, after creating your conversion action, by clicking [**Summary**](https://ads.google.com/aw/conversions) and open the enhanced conversions for leads drop down to check the same box.\


### 3. Accept the customer data terms

To accept the customer data terms click on [**Summary**](https://ads.google.com/aw/conversions), select **Settings** and click the **Customer data terms** drop down.
{% endhint %}

### Configuration

<table><thead><tr><th width="252">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><em><strong><code>Required</code></strong></em><br>Your credentials with Google Ads as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Google Ads</code></td></tr><tr><td><code>Mapping</code>    <br><code>Conversion Names</code></td><td><em><strong><code>Required</code></strong></em> <br>Map your Google Ads conversion names, where enhanced conversions are applied, with your events by setting the fields <code>Google Ads Conversion Name</code> and <code>Your event name</code> . At least one line is required. Conversion names can be found in the Google Ads interface following: <code>Goals</code> ➜ <code>Summary</code> ➜ <code>Conversion actions</code> (column).</td></tr><tr><td><code>Mapping</code>      <br><code>Custom Variables</code></td><td>Custom variables add richer data to your conversions so that you can further segment your reports. You can map your custom variable names with your values by setting the fields <code>Custom variable name</code>  and <code>Your value</code> .<br>More details are available by following this <a href="https://support.google.com/google-ads/answer/9962082?hl=en">LINK</a>.</td></tr><tr><td><code>Google Analytics</code>    <br><code>Measurement Id</code></td><td>You can add the Google Analytics "Measurement Id", which is a string like "SE23QCQ1Q8" without the intial "G-" part. It's used as an additional method to retrieve your <code>gclid</code> from available cookies.</td></tr><tr><td><code>Validate Only</code></td><td>If flagged, the request is validated but <mark style="color:orange;">not executed!</mark>. Only errors are returned, not results, in the tab <code>Event Inspector</code>.</td></tr><tr><td><code>Debug Enabled</code></td><td>If flagged, Google endpoint will perform all upload checks and return errors if any are found. If <code>false</code>, it will perform only basic input validation, skip subsequent upload checks, and return success even if no click was found for the provided user identifiers. More details are available by following this <a href="https://developers.google.com/google-ads/api/rest/reference/rest/v17/customers/uploadClickConversions?hl=en#request-body">LINK</a>.</td></tr></tbody></table>

## Quick reference

<table><thead><tr><th width="327">Commanders Act Events</th><th>Google Tracking</th></tr></thead><tbody><tr><td><code>[Any Event]</code> <strong>[1]</strong></td><td><code>customers.uploadClickConversions</code></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See [Mapping Conversion Names](google-enhanced-conversions-for-leads.md#configuration) in [Configuration](google-enhanced-conversions-for-leads.md#configuration) for more details.&#x20;
{% endhint %}

## Field mappings

{% hint style="warning" %}
At least one of the following identifiers must be provided:

* User email
* User phone
{% endhint %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Google properties are set starting from the path <mark style="color:blue;">`conversions[0]`</mark> .
{% endhint %}

<table><thead><tr><th width="424">Commanders Act Properties</th><th>Google Properties</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>orderId</code></td></tr><tr><td><p><code>partners.google.gclid</code></p><p><code>Google Analytics Measurement Id</code></p></td><td><code>gclid</code> <strong>[1]</strong> </td></tr><tr><td><code>partners.google.gbraid</code></td><td><code>gbraid</code> <strong>[2]</strong></td></tr><tr><td><code>partners.google.wbraid</code></td><td><code>wbraid</code> <strong>[3]</strong></td></tr><tr><td><p><code>partners.google.email_source</code></p><p><code>partners.google.phone_source</code></p></td><td><code>userIdentifierSource</code> <strong>[4]</strong></td></tr><tr><td><code>user.email_sha256</code></td><td><code>hashedEmail</code> <strong>[4][5]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>hashedPhoneNumber</code> <strong>[4][5]</strong></td></tr><tr><td><code>partners.google.aduserdata</code></td><td><code>consent.adUserData</code> <strong>[6]</strong></td></tr><tr><td><code>partners.google.adpers</code></td><td><code>consent.adPersonalization</code> <strong>[6]</strong></td></tr><tr><td><code>partners.google.merchant_id</code></td><td><code>cartData.merchantId</code></td></tr><tr><td><code>partners.google.feed_country_code</code></td><td><code>cartData.feedCountryCode</code></td></tr><tr><td><code>partners.google.feed_language_code</code></td><td><code>cartData.feedLanguageCode</code></td></tr><tr><td><code>partners.google.local_transaction_cost</code></td><td><code>cartData.localTransactionCost</code></td></tr><tr><td><code>items.X.id</code></td><td><code>cartData.items.X.productId</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>cartData.items.X.unitPrice</code></td></tr><tr><td><code>tems.X.quantity</code></td><td><code>cartData.items.X.quantity</code></td></tr><tr><td><code>Mapping Conversion Names</code></td><td><code>conversionAction</code> <strong>[7]</strong></td></tr><tr><td><code>value</code></td><td><code>conversionValue</code></td></tr><tr><td><code>currency</code></td><td><code>currencyCode</code></td></tr><tr><td><code>Custom variable name</code></td><td><code>conversionCustomVariable</code> <strong>[8][9]</strong></td></tr><tr><td><code>Your value</code></td><td><code>value</code> <strong>[8][10]</strong></td></tr><tr><td><code>Validate Only</code></td><td><code>validateOnly</code> <strong>[11]</strong></td></tr><tr><td><code>Debug Enabled</code></td><td><code>debugEnabled</code> <strong>[11]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See [Google Analytics Measurement Id](google-enhanced-conversions-for-leads.md#configuration) in [Configuration](google-enhanced-conversions-for-leads.md#configuration) for more details.\
**\[2]** Google click identifier for clicks associated with app conversions and originating from iOS devices starting with iOS14.\
**\[3]** Google click identifier for clicks associated with web conversions and originating from iOS devices starting with iOS14.\
**\[4]** Set in the <mark style="color:blue;">`userIdentifiers.X`</mark> . Accepted values: <mark style="color:blue;">`FIRST_PARTY`</mark> , <mark style="color:blue;">`THIRD_PARTY`</mark>  or <mark style="color:blue;">`UNSPECIFIED`</mark> . Default value: <mark style="color:blue;">`FIRST_PARTY`</mark> .\
**\[5]** Automatically hashed if provided in clear text.\
**\[6]** Accepted values: <mark style="color:blue;">`true`</mark> , <mark style="color:blue;">`1`</mark> or <mark style="color:blue;">`granted`</mark> when user granted the consent or <mark style="color:blue;">`false`</mark> , <mark style="color:blue;">`0`</mark>  or <mark style="color:blue;">`denied`</mark> otherwise. If consent is not specified use <mark style="color:blue;">`unspecified`</mark> . All string values are case insensitive. Default value <mark style="color:blue;">`granted`</mark> .\
**\[7]** Conversion resource name in the following format: <mark style="color:blue;">`customers/[CUSTOMER_ID]/conversionActions/[CONVESION_ACTION_ID]`</mark>   \
**\[8]** Set in the path <mark style="color:blue;">`customVariables.X`</mark> .\
**\[9]** Resource name of the custom variable in the following format:\
<mark style="color:blue;">`customers/[CUSTOMER_ID]/conversionCustomVariables/[VARIABLE_ID]`</mark>   \
**\[10]** Your value for the custom variable. See [Mapping Custom Variables](google-enhanced-conversions-for-leads.md#configuration) in [Configuration](google-enhanced-conversions-for-leads.md#configuration) for more details.\
**\[11]** Set in the base path.
{% endhint %}

