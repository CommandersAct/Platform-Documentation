# Google Analytics 4

Google Analytics 4 (GA4) is the latest iteration of Google's analytics tool that helps you measure the traffic and engagement across your websites and apps. Using this destination, you can enhance your existing tracking implementation to match your data collection needs with GA4.\
Your data will be sent server-side taking advantage of the [Google Measurement Protocol API](https://developers.google.com/analytics/devguides/collection/protocol/ga4) and in form of [events](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events).

{% hint style="info" %}
Google designed the Measurement Protocol with some [limitations](https://developers.google.com/analytics/devguides/collection/protocol/ga4#caveats_to_measurement_protocol), especially it does not allow to manage session.\
For [session handling](./#session-handling), you should currently setup a _**gtag**_**&#x20;config tag** that will fire on the **first page** (only) of the user's session.\
For this purpose you can use on your website the tag template **"gtag - Config with options"** as it comes with the additional configuration option to send the Google reserved event <mark style="color:blue;">`session_start`</mark> while avoid firing the event <mark style="color:blue;">`page_view`</mark> :

```javascript
gtag('config', 'G-XXXXXXXXXX', {
    ...    
    send_page_view: false
    ...
});
```
{% endhint %}

## Key features

The Google Analytics 4 destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model fits [Google's one](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional information based on your specific needs (E.g. adding custom events, custom event and user properties).
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to GA4.
* **Send all properties option**: send all your event properties to GA4 with a single click.

## Destination setup

Before you get started with this destination, make sure you have a GA4 property in your Google Analytics account. You can find more information on this topic following these detailed articles:

* [\[GA4\] Set up Analytics for a website and/or app](https://support.google.com/analytics/answer/9304153)
* [Add a Google Analytics 4 property (to a site that already has Analytics)](https://support.google.com/analytics/answer/9744165?hl=en)

### Configuration

{% hint style="warning" %}
App related fields are enabled by flagging <mark style="color:blue;">`Enable App Tracking`</mark> .\
The properties <mark style="color:blue;">`context.app.name`</mark> and <mark style="color:blue;">`context.device.type`</mark> are required for app tracking. More details on these fields are available by following this [LINK](https://doc.commandersact.com/developers/tracking/about-events/mobile-sdk-event-specificity#context.app).
{% endhint %}

{% hint style="info" %}
The user identifier should be passed in both the client-side gtag and server-side.\
For more information, you can follow these links: [\[GA4\] Measure activity across platforms with User-ID](https://support.google.com/analytics/answer/9213390) and [\[GA4\] Reporting: deduplicate user counts](https://support.google.com/analytics/answer/9355949).

When Google Signals is enabled, same device remarketing is supported. For cross-device remarketing, the user identifier is additionally required.
{% endhint %}

<table><thead><tr><th width="284">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Web API Secret</code></td><td><em><strong><code>Required for Web Data Streams</code></strong></em><br>An <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">API Secret</a> that is generated through the Google Analytics UI for a "Web Data Stream". To create this value, navigate in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Protocol API secret</code> ➜ <code>Create</code> .</td></tr><tr><td><code>Measurement Id</code></td><td><em><strong><code>Required for Web Data Streams</code></strong></em><br>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">Measurement Id</a> for a "Web Data Stream". Found in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Id</code> . E.g. "G-XXXXXXXXXX".</td></tr><tr><td><code>Android API Secret</code></td><td><em><strong><code>Required for App Android Data Streams</code></strong></em><br>An <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">API Secret</a> that is generated through the Google Analytics UI for an "App Android Data Stream". To create this value, navigate in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Protocol API secrets</code> ➜ <code>Create</code> . <strong>[1]</strong></td></tr><tr><td><code>Android Firebase App ID</code></td><td><em><strong><code>Required for App Android Data Streams</code></strong></em><br>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">Android Firebase App ID</a> for a "App Android Data Stream". Found in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>FIREBASE APP ID</code> , or in Firebase console following: <code>Project Settings</code> ➜ <code>General</code> ➜ <code>Your Apps</code> ➜ <code>App ID</code> . <strong>[1]</strong></td></tr><tr><td><code>iOS API Secret</code></td><td><em><strong><code>Required for App iOS Data Streams</code></strong></em><br>An <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">API Secret</a> that is generated through the Google Analytics UI for an "App Android Data Stream". To create this value, navigate in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Protocol API secrets</code> ➜ <code>Create</code> . <strong>[1]</strong></td></tr><tr><td><code>iOS Firebase App ID</code></td><td><em><strong><code>Required for App iOS Data Streams</code></strong></em><br>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">iOS Firebase App ID</a> for an "App iOS Data Stream". Found in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>FIREBASE APP ID</code>, or in Firebase console following: <code>Project Settings</code> ➜ <code>General</code> ➜ <code>Your Apps</code> ➜ <code>App ID</code> . <strong>[1]</strong></td></tr><tr><td><code>App Instance ID Field</code></td><td>Your property field holding the <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/sending-events?client_type=firebase#required_parameters">App Instance Id</a> for your "App Data Streams". If this is not provided, the first 32 characters of the following SHA256 hashed standard properties are used: <code>device.sdk_id</code> or <code>user.tcId</code> , in this order. <strong>[1]</strong></td></tr><tr><td><code>Send All Properties</code></td><td>When activating this option all your custom properties are also sent to GA4 in the <code>params</code> object. Properties with child/sub properties are converted into a single one using the underscore character "_" as separator (E.g. device_lifecycle_last_session_start). More details are available following this <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_post_body">LINK</a>.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>GA4 property name</code> and adding the field name holding the value in <code>Your event property</code> . E.g. if you input<code>size</code>in the <code>GA4 property name</code> and<code>items.0.product.size</code> in <code>Your event property</code> , you will have a custom event property in GA4 called <code>size</code> with a value based on the content of the field <code>items.0.product.size</code> .<br>In the column <code>Your event property path</code> you should keep the default value <code>Default (root)</code> as it better fits most scenarios. In case you select either <code>In "items" {items.X}</code> or <code>In "product" {items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and add its values as a custom item property.<br><br>To ensure that custom event properties are picked up by GA4, you must create event-scoped dimensions first. You can find more details by following this link: <a href="https://support.google.com/analytics/answer/10075209">[GA4] Custom dimensions and metrics</a>.</td></tr><tr><td><code>Custom User Properties</code></td><td><p>Map your <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/user-properties">custom user properties</a> by setting their field names in <code>GA4 property name</code> and adding the field name holding the value in <code>Your event property</code> .<br>E.g. if you input <code>customer_zipcode</code> in <code>GA4 property name</code> and <code>user.zipcode</code> in <code>Your event property</code> , you will have a custom user property in GA4 called <code>customer_zipcode</code> with a value based on the content of the field <code>user.zipcode</code> .<br></p><p>To ensure that custom user properties are picked up by GA4, you must create user-scoped dimensions first. You can find more details by following this link: <a href="https://support.google.com/analytics/answer/10075209">[GA4] Custom dimensions and metrics</a>.</p></td></tr><tr><td><code>Enable Enhanced Conversions</code></td><td>Flag this option to enable <a href="https://developers.google.com/analytics/devguides/collection/ga4/uid-data">Enhanced Conversions</a>. See our dedicated section following this <a href="./#enhanced-conversions">LINK</a>.</td></tr><tr><td><code>Enable Proxy Mode</code></td><td>Flag this option to anonymize data before sending it to Google. See our dedicated page following this <a href="https://doc.commandersact.com/features/destinations/destinations-catalog/google/google-analytics-4/google-analytics-4-proxy-mode">LINK</a>.</td></tr><tr><td><code>Client Id Cookie Name</code></td><td><p>Cookie name holding the Google Analytics <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">Client Id</a> that uniquely identifies a user instance of a web client. You can change its default value <code>_ga</code> . If this cookie is not found, <code>user.consistent_anonymous_id</code> is used.</p><p><br>The "Client Id" is the right most string in the cookie, including a single dot. E.g. see the following blue highlighted string "GA1.1.<mark style="color:blue;">XXXXXXXXXX.XXXXXXXXXX</mark><strong>".</strong></p></td></tr><tr><td><code>Engagement Time in</code><br><code>Milliseconds</code></td><td>GA4 reports only show active users who engage with your site for a non-zero amount of time. To ensure users are included in reports, you can keep the default value to 1. If you track the actual engagement time with your events, you can set the <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/sending-events?client_type=gtag#optional_parameters_for_reports"><strong>Engagement Time in Milliseconds</strong></a> with a proper value.</td></tr><tr><td><code>Override Ip</code></td><td></td></tr><tr><td><code>Enable debug mode</code></td><td>Following <code>Advanced settings</code> → <code>Debug</code>, you can flag this option to enable GA4 <a href="https://developers.google.com/analytics/devguides/collection/ga4/debug?technology=websites">Debug Mode</a> monitoring feature, sending the field <code>debug_mode</code> set to <code>true</code> on each event.</td></tr><tr><td><code>Send events for</code><br><code>validation only</code></td><td>Following <code>Advanced settings</code> → <code>Debug</code>, you can flag this option to send your events to the <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/validating-events?client_type=gtag#sending_events_for_validation">Measurement Protocol Validation Server</a> and inspect properties through our <a href="https://doc.commandersact.com/features/destinations/live-event-inspector">Event Inspector</a>. <mark style="color:orange;"><strong>Important</strong>: when this is flagged, events <strong>ARE NOT</strong> tracked by GA4.</mark></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Field available after flagging the <mark style="color:blue;">`Enable App Tracking`</mark> checkbox.
{% endhint %}

### Session handling

When providing a <mark style="color:blue;">`Measurement Id`</mark> , the session identifier is retrieved from the cookie named `_ga_<Measurement Id>` (E.g. "\_ga\_SE92QCQ4Q1", without quotes and the initial string "G-"). If the cookie is not provided or with App "Data streams", you can pass the session identifier using the property <mark style="color:blue;">`ga_session_id`</mark> : this is useful when implementing the [gtag GET API](https://developers.google.com/tag-platform/gtagjs/reference#get), on the client-side, as you can retrieve the value with the API and then pass it into <mark style="color:blue;">`ga_session_id`</mark> . When none of the above is set, the default property <mark style="color:blue;">`context.device.lifecycle.session_id`</mark> is used. More details on how sessions work in Google Analytics 4 are available following this [LINK](https://support.google.com/analytics/answer/9191807).

## Mappings for GA4 events

This destination provides automatic mapping between our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model and GA4 events. In this section, you will learn what properties are set so you can expect to see those details in GA4 reporting.

{% hint style="info" %}
More details on GA4 standard events are available following this [LINK](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events).\
To ensure that custom event properties are picked up by GA4, you must create event-scoped dimensions. You can find more details by following this link: [\[GA4\] Custom dimensions and metrics](https://support.google.com/analytics/answer/10075209).
{% endhint %}

### add\_payment\_info

| Property       | Description                                                                                                                            | Field           | Mapped with       |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ----------------- |
| Currency       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_      | _currency_        |
| Value          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_         | _value_           |
| Coupon         | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_        | _coupon_          |
| Payment Method | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                                       | _payment\_type_ | _payment\_method_ |
| Revenue        | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                 | _revenue_       | _revenue_         |
| Items          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_         | _items_           |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### add\_shipping\_info

| Property      | Description                                                                                                                            | Field            | Mapped with    |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | -------------- |
| Currency      | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_       | _currency_     |
| Value         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_          | _value_        |
| Coupon        | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_         | _coupon_       |
| Shipping Tier | <p>Type: <em><code>String</code></em><br>The shipping tier (E.g. <code>Next-day</code>) selected for delivery of the item.</p>         | _shipping\_tier_ | shipping\_tier |
| Items         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_          | _items_        |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em></p><p>Type: <em><code>String</code></em><br>The ID of the item.</p>                  | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em></p><p>Type: <em><code>String</code></em><br>The name of the item.</p>                | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### add\_to\_cart

| Property | Description                                                                                                                            | Field      | Mapped with |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _items_     |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### add\_to\_wishlist

| Property | Description                                                                                                                            | Field      | Mapped with |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Items    | <p><em><code>Required</code></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                       | _items_    | _items_     |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### begin\_checkout

| Property | Description                                                                                                                            | Field      | Mapped with |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Coupon   | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_   | _coupon_    |
| Revenue  | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                 | _revenue_  | _revenue_   |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _items_     |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### generate\_lead

| Currency       | Description                                                                                                                            | Field      | Mapped with |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Transaction Id | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                                               | _id_       | _id_        |

### login

| Property | Description                                                    | Field    | Mapped with |
| -------- | -------------------------------------------------------------- | -------- | ----------- |
| Method   | <p>Type: <em><code>String</code></em><br>The login method.</p> | _method_ | _method_    |

### page\_view

| Property      | Description                                                           | GA4 field        | Mapped with  |
| ------------- | --------------------------------------------------------------------- | ---------------- | ------------ |
| Page Location | <p>Type: <em><code>String</code></em></p><p>The current page URL.</p> | _page\_location_ | _url_        |
| Page Referrer | <p>Type: <em><code>String</code></em><br>The previous page URL.</p>   | _page\_referrer_ | _referrer_   |
| Page Title    | <p>Type: <em><code>String</code></em><br>The current page title.</p>  | _page\_title_    | _title_      |
| Page Name     | <p>Type: <em><code>String</code></em><br>The current page name.</p>   | _page\_name_     | _page\_name_ |
| Page Type     | <p>Type: <em><code>String</code></em><br>The current page type.</p>   | _page\_type_     | _page\_type_ |
| Page Path     | <p>Type: <em><code>String</code></em><br>The current page path.</p>   | _page\_path_     | _path_       |

### purchase

| Property          | Description                                                                                                                            | Field                | Mapped with        |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ------------------ |
| Currency          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_           | _currency_         |
| Value             | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_              | _value_            |
| Transaction Id    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The transaction identifier.</p>            | _id_                 | _id_               |
| Affiliation       | <p>Type: <em><code>String</code></em><br>Affiliation information.</p>                                                                  | affiliation          | _affiliation_      |
| Coupon            | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_             | _coupon_           |
| Shipping          | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                                                                            | _shipping_           | _shipping\_amount_ |
| Tax               | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                                                                               | _tax_                | _tax\_amount_      |
| Revenue           | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                 | _revenue_            | _revenue_          |
| Conversion Type   | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                                                                      | _conversion\_type_   | _type_             |
| Conversion Status | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                                    | _conversion\_status_ | _status_           |
| Conversion Url    | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                                    | _conversion\_url_    | _url_              |
| Payment Method    | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                                       | _payment\_type_      | _payment\_method_  |
| Items             | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_              | _items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### refund

| Property          | Description                                                                                                                                                    | Field                | Mapped with        |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ------------------ |
| Currency          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                         | _currency_           | _currency_         |
| Value             | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                                        | _value_              | _value_            |
| Transaction Id    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                    | _id_                 | _id_               |
| Affiliation       | <p>Type: <em><code>String</code></em><br>Affiliation information.</p>                                                                                          | affiliation          | _affiliation_      |
| Coupon            | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                                              | _coupon_             | _coupon_           |
| Shipping          | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                                                                                                    | _shipping_           | _shipping\_amount_ |
| Tax               | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                                                                                                       | _tax_                | _tax\_amount_      |
| Revenue           | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                                         | _revenue_            | _revenue_          |
| Conversion Type   | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                                                                                              | _conversion\_type_   | _type_             |
| Conversion Status | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                                                            | _conversion\_status_ | _status_           |
| Conversion Url    | <p>Type: <em><code>String</code></em><br>The conversion url.</p>                                                                                               | _conversion\_url_    | _url_              |
| Payment Method    | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                                                               | _payment\_type_      | _payment\_method_  |
| Items             | <p><em><strong><code>Required</code></strong></em> <em>for partial refunds</em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p> | _items_              | _items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### remove\_from\_cart

| Property | Description                                                                                                                            | Field      | Mapped with |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _items_     |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### search

| Property    | Description                                                                                                                     | Field          | Mapped with    |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------- | -------------- | -------------- |
| Search Term | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The term that was searched for.</p> | _search\_term_ | _search\_term_ |

### select\_content

| Property     | Description                                                                                | Field           | Mapped with     |
| ------------ | ------------------------------------------------------------------------------------------ | --------------- | --------------- |
| Content Type | <p><br>Type: <em><code>String</code></em><br>The term that was searched for.</p>           | _content\_type_ | _content\_type_ |
| Item Id      | <p>Type: <em><code>String</code></em><br>An identifier for the item that was selected.</p> | _item\_id_      | item\_id        |

### select\_item

| Property       | Description                                                                                                                       | Field              | Mapped with        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------ |
| Item List Name | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                    | _item\_list\_name_ | _item\_list\_name_ |
| Items          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p> | _items_            | _items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### sign\_up

| Property | Description                                                               | Field    | Mapped with |
| -------- | ------------------------------------------------------------------------- | -------- | ----------- |
| Method   | <p>Type: <em><code>String</code></em><br>The method used for sign up.</p> | _method_ | _method_    |

### view\_cart

| Property | Description                                                                                                                            | Field      | Mapped with |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _items_     |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _items.X.list\_position_       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### view\_item

| Property | Description                                                                                                                            | Field      | Mapped with |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _currency_  |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _value_     |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _items_     |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em></p><p>Type: <em><code>String</code></em><br>The ID of the item.</p>                  | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _items.X.list\_position_       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### view\_item\_list

| Property       | Description                                                                                                                       | Field              | Mapped with        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------ |
| Item List Name | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                    | _item\_list\_name_ | _item\_list\_name_ |
| Items          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p> | _items_            | _items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _items.X.list\_position_       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

### \[Custom Event]

You can send custom events to better fit your specific needs.

{% hint style="info" %}
More details on how you can create and manage custom events are available following this link: [\[GA4\] Modify and create events via the user interface](https://support.google.com/analytics/answer/10085872).\
The following properties are automatically attached to the event.
{% endhint %}

| Property          | Description                                                                                                                    | Field                | Mapped with        |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ | -------------------- | ------------------ |
| Currency          | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                            | _currency_           | _currency_         |
| Value             | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                                                           | _value_              | _value_            |
| Transaction Id    | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                                       | _id_                 | _id_               |
| Content Type      | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                                       | _content\_type_      | _content\_type_    |
| Conversion Type   | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                                                              | _conversion\_type_   | _type_             |
| Conversion Status | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                            | _conversion\_status_ | _status_           |
| Conversion Url    | <p>Type: <em><code>String</code></em><br>The conversion url.</p>                                                               | _conversion\_url_    | _url_              |
| Coupon            | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                              | _coupon_             | _coupon_           |
| Item Id           | <p>Type: <em><code>String</code></em><br>An identifier for the item that was selected.</p>                                     | _item\_id_           | _item\_id_         |
| Item List Name    | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                 | _item\_list\_name_   | _item\_list\_name_ |
| Method            | <p>Type: <em><code>String</code></em><br>Method used.</p>                                                                      | _method_             | _method_           |
| Page Location     | <p>Type: <em><code>String</code></em><br>The current page URL.</p>                                                             | _page\_location_     | _url_              |
| Page Referrer     | <p>Type: <em><code>String</code></em><br>The previous page URL.</p>                                                            | _page\_referrer_     | _referrer_         |
| Page Title        | <p>Type: <em><code>String</code></em><br>The current page title.</p>                                                           | _page\_title_        | _title_            |
| Page Name         | <p>Type: <em><code>String</code></em><br>The current page name.</p>                                                            | _page\_name_         | _page\_name_       |
| Page Type         | <p>Type: <em><code>String</code></em><br>The current page type.</p>                                                            | _page\_type_         | _page\_type_       |
| Page Path         | <p>Type: <em><code>String</code></em><br>The current page type.</p>                                                            | _page\_path_         | _path_             |
| Payment Method    | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                               | _payment\_type_      | _payment\_method_  |
| Revenue           | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                         | _revenue_            | _revenue_          |
| Search Term       | <p>Type: <em><code>String</code></em><br>The term that was searched for.</p>                                                   | _search\_term_       | _search\_term_     |
| Shipping Tier     | <p>Type: <em><code>String</code></em><br>The shipping tier (E.g. <code>Next-day</code>) selected for delivery of the item.</p> | _shipping\_tier_     | _shipping\_tier_   |
| Shipping          | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                                                                    | _shipping_           | _shipping\_amount_ |
| Tax               | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                                                                       | _tax_                | _tax\_amount_      |
| Items             | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                                                 | _items_              | _items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------ |
| Item Id         | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _items.X.id_                   |
| Item Name       | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _items.X.list\_position_       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _items.X.quantity_             |

## Event mapping

| Commanders Act Events | GA4 Events          |
| --------------------- | ------------------- |
| `add_payment_info`    | `add_payment_info`  |
| `add_shipping_info`   | `add_shipping_info` |
| `add_to_cart`         | `add_to_cart`       |
| `add_to_wishlist`     | `add_to_wishlist`   |
| `begin_checkout`      | `begin_checkout`    |
| `generate_lead`       | `generate_lead`     |
| `login`               | `login`             |
| `page_view`           | `page_view`         |
| `purchase`            | `purchase`          |
| `refund`              | `refund`            |
| `remove_from_cart`    | `remove_from_cart`  |
| `search`              | `search`            |
| `select_content`      | `select_content`    |
| `select_item`         | `select_item`       |
| `sign_up`             | `sign_up`           |
| `view_cart`           | `view_cart`         |
| `view_item`           | `view_item`         |
| `view_item_list`      | `view_item_list`    |
| `[Custom Event]`      | `[Custom Event]`    |

## Consent signals

{% hint style="info" %}
Google Analytics "Measurement Protocol" supports consent signals. More details are available following this [LINK](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_consent).
{% endhint %}

<table><thead><tr><th width="390">Commanders Act properties</th><th>GA4 properties</th></tr></thead><tbody><tr><td><code>user.google_consent_mode.ad_user_data</code></td><td><code>consent.ad_user_data</code></td></tr><tr><td><code>user.google_consent_mode.ad_personalization</code></td><td><code>consent.ad_personalization</code></td></tr></tbody></table>

## Enhanced conversions

When enabling this feature, you can send user-related data together with the user identifier. This can be used to improve behavior and conversion measurement. More details are available following this [LINK](https://developers.google.com/analytics/devguides/collection/ga4/uid-data?hl=en).

{% hint style="warning" %}
When [Proxy Mode](https://community.commandersact.com/platform-x/features/destinations/destinations-catalog/google/google-analytics-4/google-analytics-4-proxy-mode) is enabled, ensure the <mark style="color:blue;">`User Id`</mark> field is set to <mark style="color:blue;">`None`</mark> as its value must be present.
{% endhint %}

{% hint style="info" %}
Google properties are set starting from the path <mark style="color:blue;">`user_data`</mark>. The property <mark style="color:blue;">`user_id`</mark> is set in the base path.
{% endhint %}

<table><thead><tr><th width="334">Commanders Act Properties</th><th>Google Properties</th></tr></thead><tbody><tr><td><code>user.id</code></td><td><code>user_id</code> <strong>[*]</strong></td></tr><tr><td><code>user.email_sha256</code></td><td><code>sha256_email_address</code> <strong>[1]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>sha256_phone_number</code> <strong>[1]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>sha256_first_name</code> <strong>[1][2]</strong></td></tr><tr><td><code>user.lastname</code></td><td><code>sha256_last_name</code> <strong>[1][2]</strong></td></tr><tr><td><code>user.street</code></td><td><code>sha256_street</code> <strong>[1][2]</strong></td></tr><tr><td><code>user.city</code></td><td><code>city</code> <strong>[2][3]</strong></td></tr><tr><td><code>user.state</code></td><td><code>region</code> <strong>[2][3]</strong></td></tr><tr><td><code>user.zipcode</code></td><td><code>postal_code</code> <strong>[2][3]</strong></td></tr><tr><td><code>user.country</code></td><td><code>country</code> <strong>[2]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
&#xNAN;**\[1]** Automatically normalized and hashed, if provided in clear text.\
\&#xNAN;**\[2]** Property set starting from the path <mark style="color:blue;">`user_data.address`</mark> .\
\&#xNAN;**\[3]** Automatically normalized.
{% endhint %}

## Geographical information

{% hint style="info" %}
The following properties set in <mark style="color:blue;">`user_location`</mark> :

* <mark style="color:blue;">`city`</mark>
* <mark style="color:blue;">`region_id`</mark>
* <mark style="color:blue;">`country_id`</mark>
* <mark style="color:blue;">`subcontinent_id`</mark>
* <mark style="color:blue;">`continent_id`</mark>

and <mark style="color:blue;">`ip_override`</mark> provide geographic information. <mark style="color:blue;">`user_location`</mark> properties take precedence over <mark style="color:blue;">`ip_override`</mark> . When setting <mark style="color:blue;">`user_location`</mark> provide as many properties as possible. Google recommends <mark style="color:blue;">`country_id`</mark> and <mark style="color:blue;">`region_id`</mark> at a base minimum. If you set <mark style="color:blue;">`ip_override`</mark> Google Analytics derives geo information from the provided IP address. If you include at least one property in <mark style="color:blue;">`user_location`</mark> Google Analytics ignores <mark style="color:blue;">`ip_override`</mark> . If you don't include any property in <mark style="color:blue;">`user_location`</mark> or <mark style="color:blue;">`ip_override`</mark>, Google Analytics derives geo information from tagging events using <mark style="color:blue;">`client_id`</mark> .\
Google Analytics applies the property's [granular location data settings](https://support.google.com/analytics/answer/12002752) to the request, regardless of the geographic information sent. More details are available following this [LINK](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag\&hl=en#payload_geo_info).
{% endhint %}

<table><thead><tr><th width="334">Commanders Act Properties</th><th>Google Properties</th></tr></thead><tbody><tr><td><code>Client Id Cookie Name</code></td><td><code>client_id</code></td></tr><tr><td><code>context.device.ip</code></td><td><code>ip_override</code></td></tr><tr><td><code>user.current_location_city</code></td><td><code>city</code> <strong>[1]</strong></td></tr><tr><td><code>user.current_location_region</code></td><td><code>region_id</code> <strong>[1]</strong></td></tr><tr><td><code>user.current_location_country</code></td><td><code>country_id</code> <strong>[1]</strong></td></tr><tr><td><code>user.current_location_subcontinent</code></td><td><code>subcontinent_id</code> <strong>[1]</strong></td></tr><tr><td><code>user.current_location_continent</code></td><td><code>continent_id</code> <strong>[1]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Property set starting from the path <mark style="color:blue;">`user_location`</mark> .
{% endhint %}

## Limitations

Depending on your licence (standard or 360), sending events to GA4 has some different limitations: [https://support.google.com/analytics/answer/11202874?sjid=10370297212042052180-EU](https://support.google.com/analytics/answer/11202874?sjid=10370297212042052180-EU)
