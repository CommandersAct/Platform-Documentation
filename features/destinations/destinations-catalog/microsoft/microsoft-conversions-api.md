# Microsoft Conversions API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Microsoft Advertising](https://ads.microsoft.com/) (formerly Bing Ads, Microsoft adCenter and MSN adCenter) is an online advertising platform developed by Microsoft. Using this destination, you can leverage [Microsoft Conversions API](https://learn.microsoft.com/en-us/advertising/guides/uet-conversion-api-integration) and the [Universal Event Tracking (UET) framework](https://learn.microsoft.com/en-us/advertising/guides/uet-conversion-api-integration?view=bingads-13#universal-event-tracking-uet) to send user actions, in form of events, via server-side tracking hits, enabling features such as conversion tracking (E.g., purchases or leads), audience targeting (E.g., remarketing), automated bidding, and integration with Microsoft Bing for Commerce.

## Key features

The Microsoft Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Microsoft's Server-side UET events](https://learn.microsoft.com/en-us/advertising/guides/uet-conversion-api-integration?view=bingads-13#server-side-uet-events), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Custom events and properties**: you can freely push custom events and properties based on your specific needs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is bridged to Microsoft.
* **Support batch mode**: send multiple events in one single request.

## Destination setup

Ensure you have access to [Microsoft Advertising](https://ads.microsoft.com/).&#x20;

{% hint style="info" %}
This destination can be used as a stand-alone or together with the [UET client-side JavaScript tracking](https://help.ads.microsoft.com/#apex/ads/en/56686/2).\
While data is captured using this destination, a client-side user identification sync pixel can also be used to connect Microsoft and customer-assigned user identifiers. The sync pixel can be found [in our client-side template library](https://doc.commandersact.com/features/sources/sources-catalog/web/containers/user-guides-for-browser-side-platform/tags/add-tags) with the name <mark style="color:blue;">`Bing - Client-side id-sync and data capture`</mark>  and is recommended for conversion measurement as it’s required for remarketing and audience building because these features rely on user identity resolution. More details are available at the following [LINK](https://learn.microsoft.com/en-us/advertising/guides/uet-conversion-api-integration?view=bingads-13#client-side-id-sync).
{% endhint %}

{% hint style="warning" %}
In the scenario where you use the same `UET Tag Id` (See [Configuration](microsoft-conversions-api.md#configuration)) for both UET client-side JavaScript and this destination, it's important to set up the deduplication. Please refer to this [LINK](https://learn.microsoft.com/en-us/advertising/guides/uet-conversion-api-integration?view=bingads-13#custom-events), showing how to set the value for the `event_id` in the UET client-side JavaScript. The `eventId` (See [Field mappings](microsoft-conversions-api.md#field-mappings)) can be set using the "Smart Mapping" field `Event Id` . Both `event_id`  and `eventId` must be set with the same value.
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em><br>Input your <code>Access Token</code>. You can find it in <a href="https://help.ads.microsoft.com/apex/index/3/en/56705">Microsoft Advertising Ads UI</a> by selecting <code>Conversions</code>  (left-side menu) → <code>EUT tag</code> → hover over the tag name and click the pencil → In <code>Edit UET tag</code> , click <code>Save and next</code>  → Select <code>Use Conversions API</code> .</td></tr><tr><td><code>UET Tag Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your <code>UET Tag Id</code> . You can find it in <a href="https://help.ads.microsoft.com/apex/index/3/en/56705">Microsoft Advertising Ads UI</a> by selecting <code>Conversions</code>  (left-side menu) → <code>EUT tag</code>  → column <code>Tag ID</code> .</td></tr><tr><td><code>Click Id Cookie Name</code></td><td>The <code>msclkid</code> (Click Id) is used in conversion attribution and is generated at ad click time. This id is appended to the landing page URL when <a href="https://help.ads.microsoft.com/#apex/ads/en/60125/2-500">Microsoft auto-tagging</a> is enabled. It should be stored in a first party cookie and persisted for each user for 90 days or until the user generates a new <code>msclkid</code> by clicking on another ad, whichever comes first. Input your cookie name holding the value. Default: <code>_uetmsclkid</code>. More details are available at the following <a href="https://help.ads.microsoft.com/#apex/ads/en/60000/2">LINK</a>. You can also add the value in a property and use the "Smart Mapping" field <code>Microsoft Msclkid</code> which has priority over the <code>Click Id Cookie Name</code> . This destination also tries to get the value from the page URL using the property mapped in the "Smart Mapping" field <code>Page URL</code> .</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Microsoft Event Types |
| --------------------- | --------------------- |
| `page_view`           | `pageLoad`            |
| `[Any other event]`   | `custom`              |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="396.6685580062746">Commanders Act Properties</th><th>Microsoft Properties</th></tr></thead><tbody><tr><td><code>(event_name)</code></td><td><code>eventType</code> <strong>[1]</strong></td></tr><tr><td><code>context.event_id</code></td><td><code>eventId</code> <strong>[2]</strong></td></tr><tr><td><code>event_name</code></td><td><code>eventName</code></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>eventTime</code></td></tr><tr><td><code>context.page.url</code></td><td><code>eventSourceUrl</code></td></tr><tr><td><code>context.device.lifecycle.session_id</code></td><td><code>pageLoadId</code> <strong>[3]</strong></td></tr><tr><td><code>context.page.referrer</code></td><td><code>referrerUrl</code></td></tr><tr><td><code>context.page.title</code></td><td><code>pageTitle</code></td></tr><tr><td><code>partners.microsoft.keyword</code></td><td><code>keywords</code></td></tr><tr><td><code>partners.microsoft.ad_storage_consent</code></td><td><code>adStorageConsent</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>clientUserAgent</code> <strong>[4]</strong></td></tr><tr><td><code>user.consistent_anonymous_id</code></td><td><code>anonymousId</code></td></tr><tr><td><code>user.id</code></td><td><code>externalId</code></td></tr><tr><td><code>user.email</code></td><td><code>em</code> <strong>[5]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>ph</code> <strong>[5][6]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>clientIpAddress</code></td></tr><tr><td><p><code>partners.microsoft.msclkid</code></p><p><code>Click Id Cookie Name</code></p><p><code>(context.page.url)</code></p></td><td><code>msclkid</code> <strong>[7]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>gaid</code> <strong>[8]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>idfa</code> <strong>[9]</strong></td></tr><tr><td><code>event_category</code></td><td><code>eventCategory</code> <strong>[10]</strong></td></tr><tr><td><code>event_label</code></td><td><code>eventLabel</code> <strong>[10]</strong></td></tr><tr><td><code>value</code></td><td><p><code>eventValue</code> <strong>[10]</strong></p><p><code>ecommTotalValue</code> <strong>[10]</strong></p><p><code>hotelData.totalPrice</code> <strong>[10]</strong></p></td></tr><tr><td><code>revenue</code></td><td><code>value</code>  <strong>[10]</strong><br><code>hotelData.basePrice</code> <strong>[10]</strong></td></tr><tr><td><code>search_term</code></td><td><code>searchTerm</code> <strong>[10]</strong></td></tr><tr><td><code>id</code></td><td><code>transactionId</code> <strong>[10]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[10]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>items.X.id</code> <strong>[10]</strong></td></tr><tr><td><code>items.X.product.price</code></td><td><code>items.X.price</code> <strong>[10]</strong></td></tr><tr><td><code>items.X.quantity</code></td><td><code>items.X.quantity</code> <strong>[10]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>items.X.name</code> <strong>[10]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>itemIds</code> <strong>[10][11]</strong></td></tr><tr><td><p><code>(page_type)</code></p><p><code>(event_name)</code></p></td><td><code>pageType</code> <strong>[10][12]</strong></td></tr><tr><td><code>item_list_name</code></td><td><code>ecommCategory</code> <strong>[10]</strong></td></tr><tr><td><code>partners.microsoft.hotel_checkin_date</code></td><td><code>hotelData.checkinDate</code> <strong>[10]</strong></td></tr><tr><td><code>partners.microsoft.hotel_checkout_date</code></td><td><code>hotelData.checkoutDate</code> <strong>[10]</strong></td></tr><tr><td><code>partners.microsoft.hotel_length_stay</code></td><td><code>hotelData.lengthOfStay</code> <strong>[10]</strong></td></tr><tr><td><code>partners.microsoft.hotel_partner_id</code></td><td><code>hotelData.partnerHotelId</code> <strong>[10]</strong></td></tr></tbody></table>

{% hint style="info" %}
> **\[1]** See [Quick reference](microsoft-conversions-api.md#quick-reference) for more details.\
> &#xNAN;**\[2]** Used for deduplication. See [Destination setup](microsoft-conversions-api.md#destination-setup) for more details.\
> &#xNAN;**\[3]** Page load identifier that links your custom events from the same page. Format as\
> a v4 UUID.\
> **\[4]** Set in the `userData` .\
> &#xNAN;**\[5]** Automatically normalized and hashed via SHA256 when provided in clear text.\
> &#xNAN;**\[6]** Normalized using E.164 format with country code.\
> &#xNAN;**\[7]** Priority on the left column. You use the field `Click Id Cookie Name`  (See [Configuration](microsoft-conversions-api.md#configuration)) to set a different cookie name instead of the default `_uetmsclkid` . The value will be automatically retrieved from the `context.page.url` if present.\
> &#xNAN;**\[8]** Set if `context.device.os.name`  is set with `Android`  (Case insensitive).\
> &#xNAN;**\[9]** Set if `context.device.os.name`  is set with `iOS`  (Case insensitive).\
> &#xNAN;**\[10]** Set in the `customData` .\
> &#xNAN;**\[11]** All product identifiers are taken into account.\
> &#xNAN;**\[12]** Priority on the left column. This is set depending on the following:\
> • If `page_type`  is `home` , `product` , `cart` , `category` , `other` , `purchase` or `searchresults`  then `pageType`  is set with the same value .\
> • If `page_type`  is `product_list`  then `pageType`  is `category` .\
> • If `page_type`  is `funnel_confirmation`  then `pageType`  is `purchase` .\
> • If `page_type`  is `search`  then `pageType`  is `searchresults` .\
> • If `event_name`  is `search`  then `pageType`  is `searchresults` .\
> • If `event_name`  is `view_item_list`  then `pageType`  is `category` .\
> • If `event_name`  is `view_item`  then `pageType`  is `product` .\
> • If `event_name`  is `view_item`  or `add_to_cart`  then `pageType`  is `product` .\
> • If `event_name`  is `view_cart`  then `pageType`  is `cart` .\
> • If `event_name`  is `purchase`  then `pageType`  is `purchase` .
{% endhint %}





