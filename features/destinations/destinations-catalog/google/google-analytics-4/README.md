# Google Analytics 4

Google Analytics 4 (GA4) is the latest iteration of Google's analytics tool that helps you measure the traffic and engagement across your websites and apps. Using this destination, you can enhance your existing tracking implementation to match your data collection needs with GA4.\
Your data will be sent server-side taking advantage of the [Google Measurement Protocol API](https://developers.google.com/analytics/devguides/collection/protocol/ga4) and in form of [events](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events).

{% hint style="info" %}
For [session handling](./#session-handling), it's recommended to deploy our client-side tag template "gtag - Config with options" as it comes with the additional configuration option to send the Google reserved event<mark style="color:blue;">`session_start`</mark>while avoid firing the event<mark style="color:blue;">`page_view`</mark>:

```javascript
gtag('config', 'G-XXXXXXXXXX', {
    ...    
    send_page_view: false
    ...
});
```

More details are available following [our dedicated section](./#session-handling).&#x20;

The user identifier should be passed in both the client-side gtag and server-side.\
For more information, you can follow these links: [\[GA4\] Measure activity across platforms with User-ID](https://support.google.com/analytics/answer/9213390) and [\[GA4\] Reporting: deduplicate user counts](https://support.google.com/analytics/answer/9355949).

When Google Signals is enabled, same device remarketing is supported. For cross-device remarketing, the user identifier is additionally required.

Geographic information is only available via automatic collection from gtag, Google Tag Manager, or Google Analytics for Firebase.
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

{% hint style="info" %}
App related fields are enabled by flagging<mark style="color:blue;">`Enable App Tracking`</mark>.
{% endhint %}

<table><thead><tr><th width="350">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>API Secret</code></td><td><p><em><strong><code>Required for Web Data Streams</code></strong></em></p><p>An <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">API Secret</a> that is generated through the Google Analytics UI for a "Web Data Stream". To create this value, navigate in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Protocol API secret</code> ➜ <code>Create</code>.</p></td></tr><tr><td><code>Measurement Id</code></td><td><p><em><strong><code>Required for Web Data Streams</code></strong></em></p><p>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">Measurement Id</a> for a "Web Data Stream". Found in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Id</code>. E.g. "G-XXXXXXXXXX".</p></td></tr><tr><td><code>Android API Secret</code></td><td><p><em><strong><code>Required for App Android Data Streams</code></strong></em></p><p>An <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">API Secret</a> that is generated through the Google Analytics UI for an "App Android Data Stream". To create this value, navigate in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Protocol API secrets</code> ➜ <code>Create</code>.</p></td></tr><tr><td><code>Android Firebase App ID</code></td><td><p><em><strong><code>Required for App Android Data Streams</code></strong></em></p><p>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">Android Firebase App ID</a> for a "App Android Data Stream". Found in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>FIREBASE APP ID</code>, or in Firebase console following: <code>Project Settings</code>  ➜ <code>General</code> ➜ <code>Your Apps</code> ➜ <code>App ID</code>.</p></td></tr><tr><td><code>iOS API Secret</code></td><td><p><em><strong><code>Required for App iOS Data Streams</code></strong></em></p><p>An <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">API Secret</a> that is generated through the Google Analytics UI for an "App Android Data Stream". To create this value, navigate in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>Measurement Protocol API secrets</code> ➜ <code>Create</code>.</p></td></tr><tr><td><code>iOS Firebase App ID</code></td><td><p><em><strong><code>Required for App iOS Data Streams</code></strong></em></p><p>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=firebase#payload_query_parameters">iOS Firebase App ID</a> for an "App iOS Data Stream". Found in the Google Analytics interface following:<br><code>Admin</code> ➜ <code>Data Streams</code> ➜ Choose your stream ➜ <code>FIREBASE APP ID</code>, or in Firebase console following: <code>Project Settings</code>  ➜ <code>General</code> ➜ <code>Your Apps</code> ➜ <code>App ID</code>.</p></td></tr><tr><td><code>App Instance ID Field</code></td><td>Your property field holding the <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/sending-events?client_type=firebase#required_parameters">App Instance Id</a> for your "App Data Streams". If this is not provided, the first 32 characters of the following SHA256 hashed standard properties are used: <code>device.sdk_id</code> or <code>properties.user.tcId</code>, in this order.</td></tr><tr><td><code>Send All Properties</code></td><td>When activating this option all properties included in the root of your Commanders Act events are also sent to GA4 in the <code>params</code> object. Properties with child/sub properties are converted into a single one using the underscore character "_" as separator (E.g. device_lifecycle_last_session_start). More details are available following this <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_post_body">LINK</a>.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>GA4 property name</code> and adding the field name holding the value in <code>Your event property</code>. E.g. if you input<code>size</code>in the <code>GA4 property name</code> and<code>properties.items.0.product.size</code> <strong>[1]</strong> in <code>Your event property</code>, you will have a custom event property in GA4 called<code>size</code>with a value based on the content of the field<code>properties.items.0.product.size</code>. <br>To ensure that custom event properties are picked up by GA4, you must create event-scoped dimensions first. You can find more details by following this link: <a href="https://support.google.com/analytics/answer/10075209">[GA4] Custom dimensions and metrics</a>.</td></tr><tr><td><code>Custom User Properties</code></td><td><p>Map your <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/user-properties">custom user properties</a> by setting their field names in <code>User property name</code> and adding the field name holding the value in <code>Commanders Act event property or static value</code>.<br>E.g. if you input<code>customer_zipcode</code>in <code>User property name</code> and<code>properties.user.zipcode</code> <strong>[1]</strong> in <code>Commanders Act event property or static value</code>, you will have a custom user property in GA4 called<code>customer_zipcode</code>with a value based on the content of the field<code>properties.user.zipcode</code>. You also have the option to set a static string/numeric value in <code>Commanders Act event property or static value</code>.<br></p><p>To ensure that custom user properties are picked up by GA4, you must create user-scoped dimensions first. You can find more details by following this link: <a href="https://support.google.com/analytics/answer/10075209">[GA4] Custom dimensions and metrics</a>.</p></td></tr><tr><td><code>Client Id Cookie Name</code></td><td><p>Cookie name holding the Google Analytics <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">Client Id</a> that uniquely identifies a user instance of a web client. You can change its default value: "<em>_ga</em>".</p><p><br>The "Client Id" is the right most string in the cookie, including a single dot. E.g. see the following blue highlighted string "GA1.1.<mark style="color:blue;">XXXXXXXXXX.XXXXXXXXXX</mark><strong>".</strong> </p></td></tr><tr><td><code>Engagement Time in Milliseconds</code></td><td>GA4 reports only show active users who engage with your site for a non-zero amount of time. To ensure users are included in reports, you can keep the default value to 1. If you track the actual engagement time with your events, you can set the <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/sending-events?client_type=gtag#optional_parameters_for_reports"><strong>Engagement Time in Milliseconds</strong></a> with a proper value.</td></tr><tr><td><code>Enable debug mode</code></td><td>Under Debug View, you can flag this option to enable <a href="https://developers.google.com/analytics/devguides/collection/ga4/debug?technology=websites">Debug Mode</a>, sending the field "<em>debug_mode</em>" set to "<em>true</em>" on each event. It enables GA4 <a href="https://support.google.com/analytics/answer/7201382">DebugView</a> monitoring feature.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

### Session handling

When providing a<mark style="color:blue;">`Measurement Id`</mark>, the session identifier is retrieved from the cookie named `_ga_<Measurement Id>` (E.g. "\_ga\_SE92QCQ4Q1", without quotes and the initial string "G-"). If the cookie is not provided or with App "Data streams", the default property `context.device.lifecycle.session_id` is used. More details on how sessions work in Google Analytics 4 are available following this [LINK](https://support.google.com/analytics/answer/9191807).

## Mappings for GA4 events

This destination provides automatic mapping between our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model and GA4 events. In this section, you will learn what properties are set so you can expect to see those details in GA4 reporting.

{% hint style="info" %}
More details on GA4 standard events are available following this [LINK](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events).\
To ensure that custom event properties are picked up by GA4, you must create event-scoped dimensions. You can find more details by following this link: [\[GA4\] Custom dimensions and metrics](https://support.google.com/analytics/answer/10075209).
{% endhint %}

### add\_payment\_info

| Property       | Description                                                                                                                            | Field           | Mapped with                  |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ---------------------------- |
| Currency       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_      | _properties.currency_        |
| Value          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_         | _properties.value_           |
| Coupon         | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_        | _properties.coupon_          |
| Payment Method | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                                       | _payment\_type_ | _properties.payment\_method_ |
| Revenue        | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                 | _revenue_       | _properties.revenue_         |
| Items          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_         | _properties.items_           |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### add\_shipping\_info

| Property      | Description                                                                                                                            | Field            | Mapped with               |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ------------------------- |
| Currency      | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_       | _properties.currency_     |
| Value         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_          | _properties.value_        |
| Coupon        | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_         | _properties.coupon_       |
| Shipping Tier | <p>Type: <em><code>String</code></em><br>The shipping tier (E.g. <code>Next-day</code>) selected for delivery of the item.</p>         | _shipping\_tier_ | properties.shipping\_tier |
| Items         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_          | _properties.items_        |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em></p><p>Type: <em><code>String</code></em><br>The ID of the item.</p>                  | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em></p><p>Type: <em><code>String</code></em><br>The name of the item.</p>                | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### add\_to\_cart

| Property | Description                                                                                                                            | Field      | Mapped with           |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### add\_to\_wishlist

| Property | Description                                                                                                                            | Field      | Mapped with           |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Items    | <p><em><code>Required</code></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                       | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### begin\_checkout

| Property | Description                                                                                                                            | Field      | Mapped with           |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Coupon   | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_   | _properties.coupon_   |
| Revenue  | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                 | _revenue_  | _properties.revenue_  |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### generate\_lead

| Currency       | Description                                                                                                                            | Field      | Mapped with           |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Transaction Id | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                                               | _id_       | _properties.id_       |

### login

| Property | Description                                                    | Field    | Mapped with         |
| -------- | -------------------------------------------------------------- | -------- | ------------------- |
| Method   | <p>Type: <em><code>String</code></em><br>The login method.</p> | _method_ | _properties.method_ |

### page\_view

| Property      | Description                                                           | GA4 field        | Mapped with             |
| ------------- | --------------------------------------------------------------------- | ---------------- | ----------------------- |
| Page Location | <p>Type: <em><code>String</code></em></p><p>The current page URL.</p> | _page\_location_ | _properties.url_        |
| Page Referrer | <p>Type: <em><code>String</code></em><br>The previous page URL.</p>   | _page\_referrer_ | _properties.referrer_   |
| Page Title    | <p>Type: <em><code>String</code></em><br>The current page title.</p>  | _page\_title_    | _properties.title_      |
| Page Name     | <p>Type: <em><code>String</code></em><br>The current page name.</p>   | _page\_name_     | _properties.page\_name_ |
| Page Type     | <p>Type: <em><code>String</code></em><br>The current page type.</p>   | _page\_type_     | _properties.page\_type_ |
| Page Path     | <p>Type: <em><code>String</code></em><br>The current page path.</p>   | _page\_path_     | _properties.path_       |

### purchase

| Property          | Description                                                                                                                            | Field                | Mapped with                  |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ---------------------------- |
| Currency          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_           | _properties.currency_        |
| Value             | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_              | _properties.value_           |
| Transaction Id    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The transaction identifier.</p>            | _id_                 | _properties.id_              |
| Affiliation       | <p>Type: <em><code>String</code></em><br>Affiliation information.</p>                                                                  | affiliation          | _properties.affiliation_     |
| Coupon            | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                      | _coupon_             | _properties.coupon_          |
| Shipping          | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                                                                            | _shipping_           | properties.shipping\_amount  |
| Tax               | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                                                                               | _tax_                | properties.tax\_amount       |
| Revenue           | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                 | _revenue_            | _properties.revenue_         |
| Conversion Type   | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                                                                      | _conversion\_type_   | _properties.type_            |
| Conversion Status | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                                    | _conversion\_status_ | _properties.status_          |
| Conversion Url    | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                                    | _conversion\_url_    | _properties.url_             |
| Payment Method    | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                                       | _payment\_type_      | _properties.payment\_method_ |
| Items             | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_              | _properties.items_           |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### refund

| Property          | Description                                                                                                                                                    | Field                | Mapped with                 |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | --------------------------- |
| Currency          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                         | _currency_           | _properties.currency_       |
| Value             | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                                        | _value_              | _properties.value_          |
| Transaction Id    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                    | _id_                 | _properties.id_             |
| Affiliation       | <p>Type: <em><code>String</code></em><br>Affiliation information.</p>                                                                                          | affiliation          | _properties.affiliation_    |
| Coupon            | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                                                              | _coupon_             | _properties.coupon_         |
| Shipping          | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                                                                                                    | _shipping_           | properties.shipping\_amount |
| Tax               | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                                                                                                       | _tax_                | properties.tax\_amount      |
| Revenue           | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                                                         | _revenue_            | _properties.revenue_        |
| Conversion Type   | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                                                                                              | _conversion\_type_   | _properties.type_           |
| Conversion Status | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                                                            | _conversion\_status_ | _properties.status_         |
| Conversion Url    | <p>Type: <em><code>String</code></em><br>The conversion url.</p>                                                                                               | _conversion\_url_    | _properties.url_            |
| Payment Method    | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                                                               | _payment\_type_      | properties.payment\_method  |
| Items             | <p><em><strong><code>Required</code></strong></em> <em>for partial refunds</em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p> | _items_              | _properties.items_          |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### remove\_from\_cart

| Property | Description                                                                                                                            | Field      | Mapped with           |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### search

| Property    | Description                                                                                                                     | Field          | Mapped with               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------- | -------------- | ------------------------- |
| Search Term | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The term that was searched for.</p> | _search\_term_ | _properties.search\_term_ |

### select\_content

| Property     | Description                                                                                | Field           | Mapped with                |
| ------------ | ------------------------------------------------------------------------------------------ | --------------- | -------------------------- |
| Content Type | <p><br>Type: <em><code>String</code></em><br>The term that was searched for.</p>           | _content\_type_ | _properties.content\_type_ |
| Item Id      | <p>Type: <em><code>String</code></em><br>An identifier for the item that was selected.</p> | _item\_id_      | properties.item\_id        |

### select\_item

| Property       | Description                                                                                                                       | Field              | Mapped with                   |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------- |
| Item List Name | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                    | _item\_list\_name_ | _properties.item\_list\_name_ |
| Items          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p> | _items_            | _properties.items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### sign\_up

| Property | Description                                                               | Field    | Mapped with         |
| -------- | ------------------------------------------------------------------------- | -------- | ------------------- |
| Method   | <p>Type: <em><code>String</code></em><br>The method used for sign up.</p> | _method_ | _properties.method_ |

### view\_cart

| Property | Description                                                                                                                            | Field      | Mapped with           |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### view\_item

| Property | Description                                                                                                                            | Field      | Mapped with           |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------- |
| Currency | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| Value    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Items    | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em></p><p>Type: <em><code>String</code></em><br>The ID of the item.</p>                  | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### view\_item\_list

| Property       | Description                                                                                                                       | Field              | Mapped with                   |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------- |
| Item List Name | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                    | _item\_list\_name_ | _properties.item\_list\_name_ |
| Items          | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>Array</code></em><br>The list of products of the event.</p> | _items_            | _properties.items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The ID of the item.</p>                     | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p><em><strong><code>Required</code></strong></em><br>Type: <em><code>String</code></em><br>The name of the item.</p>                   | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### \[Custom Event]

You can send custom events to better fit your specific needs.

{% hint style="info" %}
More details on how you can create and manage custom events are available following this link: [\[GA4\] Modify and create events via the user interface](https://support.google.com/analytics/answer/10085872).\
The following properties are automatically attached to the event.
{% endhint %}

| Property          | Description                                                                                                                    | Field                | Mapped with                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ | -------------------- | ----------------------------- |
| Currency          | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                            | _currency_           | _properties.currency_         |
| Value             | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                                                           | _value_              | _properties.value_            |
| Transaction Id    | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                                       | _id_                 | _properties.id_               |
| Content Type      | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>                                                       | _content\_type_      | _properties.content\_type_    |
| Conversion Type   | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                                                              | _conversion\_type_   | _properties.type_             |
| Conversion Status | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                                                            | _conversion\_status_ | _properties.status_           |
| Conversion Url    | <p>Type: <em><code>String</code></em><br>The conversion url.</p>                                                               | _conversion\_url_    | _properties.url_              |
| Coupon            | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                              | _coupon_             | _properties.coupon_           |
| Item Id           | <p>Type: <em><code>String</code></em><br>An identifier for the item that was selected.</p>                                     | _item\_id_           | _properties.item\_id_         |
| Item List Name    | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                 | _item\_list\_name_   | _properties.item\_list\_name_ |
| Method            | <p>Type: <em><code>String</code></em><br>Method used.</p>                                                                      | _method_             | _properties.method_           |
| Page Location     | <p>Type: <em><code>String</code></em><br>The current page URL.</p>                                                             | _page\_location_     | _properties.url_              |
| Page Referrer     | <p>Type: <em><code>String</code></em><br>The previous page URL.</p>                                                            | _page\_referrer_     | _properties.referrer_         |
| Page Title        | <p>Type: <em><code>String</code></em><br>The current page title.</p>                                                           | _page\_title_        | _properties.title_            |
| Page Name         | <p>Type: <em><code>String</code></em><br>The current page name.</p>                                                            | _page\_name_         | _properties.page\_name_       |
| Page Type         | <p>Type: <em><code>String</code></em><br>The current page type.</p>                                                            | _page\_type_         | _properties.page\_type_       |
| Page Path         | <p>Type: <em><code>String</code></em><br>The current page type.</p>                                                            | _page\_path_         | _properties.path_             |
| Payment Method    | <p>Type: <em><code>String</code></em><br>The payment method.</p>                                                               | _payment\_type_      | _properties.payment\_method_  |
| Revenue           | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>                                                         | _revenue_            | _properties.revenue_          |
| Search Term       | <p>Type: <em><code>String</code></em><br>The term that was searched for.</p>                                                   | _search\_term_       | _properties.search\_term_     |
| Shipping Tier     | <p>Type: <em><code>String</code></em><br>The shipping tier (E.g. <code>Next-day</code>) selected for delivery of the item.</p> | _shipping\_tier_     | _properties.shipping\_tier_   |
| Shipping          | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                                                                    | _shipping_           | properties.shipping\_amount   |
| Tax               | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                                                                       | _tax_                | properties.tax\_amount        |
| Items             | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                                                 | _items_              | _properties.items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| Item Id         | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| Item Name       | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | properties.items.X.list\_position         |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

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

## Limitations

Sending events to GA4 has the following limitations:

* Events can have a maximum of 25 parameters.
* Events can have a maximum of 25 user properties.
* User property names must be 24 characters or fewer.
* User property values must be 36 characters or fewer.
* Event names must be 40 characters or fewer, may only contain alpha-numeric characters and underscores, and must start with an alphabetic character.
* Parameter names (including item parameters) must be 40 characters or fewer, may only contain alpha-numeric characters and underscores, and must start with an alphabetic character.
* Parameter values (including item parameter values) must be 100 character or fewer.
* Item parameters can have a maximum of 10 custom parameters.
