---
description: Aka Facebook CAPI
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Facebook Conversions API

[Facebook ](https://www.facebook.com/)is an online social media and social networking service owned by [Meta](https://www.meta.com).\
This destination allows you to push every kind of event directly to Facebook through API: by sending online and offline conversions to you can increase the reach and accuracy of your campaigns.

You can, for example, not send campaigns related to a specific product to users who already bought it, or you can also send campaigns to users who bought a specific product in cross-sell logic.

## How to send events to Facebook?

Facebook developed an API called 'Facebook Conversions API' [https://developers.facebook.com/docs/marketing-api/conversions-api](https://developers.facebook.com/docs/marketing-api/conversions-api)

You need a Facebook Business Manager account [https://business.facebook.com/](https://business.facebook.com/)

Then on the menu, click on 'Events Manager':

![Events Manager](../../../../.gitbook/assets/capture-de-cran-2020-10-29-a-10.30.43.png)

Here you have to create a new Web Pixel:

![New web Pixel](../../../../.gitbook/assets/capture-de-cran-2020-10-29-a-12.01.41.png)

Select Conversions API and give a name to your connection:

![](../../../../.gitbook/assets/capture-de-cran-2020-10-29-a-12.02.46.png)

Now your pixel is created and you will have access to the IDs needed on our connector.

## Where can I find the Pixel ID?

You need to fill the pixel ID on our connector, it is the ID of the pixel you just created on steps above.

You can find this ID when you click on the pixel's name and on the right of the graph activities. You can find it also on the settings tab.

![Find the Pixel ID](../../../../.gitbook/assets/capture-de-cran-2020-10-29-a-12.13.54.png)

You can now copy and paste this ID on our connector.

Then you need the Access Token

## Where can I find the access token?

You can set your access token in two ways:

1. Facebook Login For Business Authentication
2. Generate a long-lived token

{% hint style="info" %}
If you configure both, the "Facebook Login For Business Authentication" will be prioritized.
{% endhint %}

### Facebook Login For Business Authentication

{% hint style="success" %}
This is the recommended authentication method.
{% endhint %}

1. In [your Commanders Act account](https://app.commandersact.com/), access `(1) Administration` → `(2) Connector Credentials` or click the link `add a new account` in the destination settings.\
   \
   ![](../../../../.gitbook/assets/token_1.png)\\
2. Click `(3) Add connector credentials` on the top right:\
   \
   ![](../../../../.gitbook/assets/token_2.png)\\
3. Select `(4) Facebook Ads`\
   \
   ![](../../../../.gitbook/assets/token_3.png)\\
4. Log in with your Facebook account credentials.
5. Go to your destination settings and select your added credentials in the drop-down menu under `(5) API Authentication` → `(6) Credentials`\
   \
   ![](../../../../.gitbook/assets/token_4.png)
6. Save your destination settings.

### Generate a long-lived token

1. Go to [Meta Event Manager](https://www.facebook.com/events_manager2/)
2. On the left menu, select `(1)` `Data sources` .

![](../../../../.gitbook/assets/facebook_capi_1.png)

3. Locate your `(2)` existing dataset and select it or [create a new dataset](https://www.facebook.com/business/help/5818684664831465?id=490360542427371).

![](../../../../.gitbook/assets/facebook_capi_2.png)

4. Click the tab `(3)` `Settings`

![](../../../../.gitbook/assets/facebook_capi_3.png)

5. Locate the link `(4)` `Generate access token` and click it to generate an access token

![](../../../../.gitbook/assets/facebook_capi_4.png)

{% hint style="warning" %}
If you can't click the link "Generate access token" then you don't have the admin rights.
{% endhint %}

6. Copy and paste your access token into the field `API Access Token` in your destination and save your destination settings.

## How to manage consents?

* Only events with a consent will be sent to Facebook
* Only conversions with personal information (email and/or phone number...) will be sent to Facebook

### For customers with our product TRUST Commander:

TRUST Commander is our Consent Management Platform. (More information: [https://www.commandersact.com/en/solutions/trustcommander/](https://www.commandersact.com/en/solutions/trustcommander/))

On the connector, the consent is managed with the field 'User Consent Category'. You should enter a category ID, the one corresponding to Facebook (advertising) on Trust consent categories.

### For customers without our product TRUST Commander:

We should distinguish 3 cases:

* Your online events are collected through our Commanders Act event's tag: You have to provide, in the event tags, the list of category ids consented by the user, through the `consent_categories` property.
* You are pushing your events to us through API or CSV file: a field `consent_categories` must be added on the JSON or CSV to precise the consent category IDs of the user. Then inside the connector setting, use the field 'User Consent Category' to enter a category ID, the one corresponding to Facebook (advertising)
*   You already manage consents on your side and you only send us, from your server,

    events that obtained the consent for the category advertising.\
    In this case, do not fill the field ‘User Consent Category’ in the connector.

## How the deduplication between the pixel and server is managed?

Using both the pixel and server is recommended per Facebook as it could avoid losing data.

To make it works, you should have the same configuration for both the pixel and server, using same Facebook parameters.

{% hint style="warning" %}
**event\_id** should be the same
{% endhint %}

On the pixel, _`event_id`_ is automatically generated by our Commanders Act Tag and we retrieve the same value for the server on `integrations.facebook.event_id`. As a result, these 2 values should be the same. _`Event_name`_ should be the same also.

_`Fbp`_ parameter is automatically retrieved to keep the same value between pixel and server.

Deduplication works when the same event is sent _first_ from the browser and _then_ from the server, otherwise it creates a duplicate.\
Events are pushed in real-time.

### Examples

On pixel:

```
fbq('track', 'AddToCart', {
  value: #CARTVALUE#,
  currency: #CURRENCY#,
  contents: fb_addtocart_products,
  content_type: 'product'
}, { eventID: tC.uniqueEventId });
```

`eventID: tC.uniqueEventId` is automatically generated.

On server:

```
integrations.facebook.event_id
```

`integrations.facebook.event_id` automatically retrieves the eventID value coming from the pixel (`eventID: tC.uniqueEventId`) for standard events.

## Mappings to Facebook Standard Events

The _Facebook CAPI Destination_ will turn the _Commanders Act_ event like...

```json
{
  "event_name": "purchase",
  "id": "purchase_id_1234",
  "type": "online",
  "user": {
    "email": "user@example.com",
    "id": "user_example_id",
    "tcId": "202205231352367212315156",
    "consistent_anonymous_id": "202205231352367212315156",
    "consent_categories": [ "1", "2", "3", "4" ]
  }
  "value": 246.9,
  "currency": "EUR",
  "items": [
    {
      "product": {
        "id": "product123"
      },
      "price": "123.45",
      "id": "ET",
      "item_category": "Car",
      "item_quantity": 2
    }
  ],
  "context": {
    "event_id": "1a01c3e940f150eb9b8c542587f1abfd8f0e1cc1f",
    "event_timestamp": 1707830130234,
    "page": {
      "location": {
        "href": "https://site.com/path?s=2",
        "hostname": "site.com",
        "pathname": "/path",
        "search": "?s=2"
      },
      "url": "https://site.com/path?s=2"
    },
    "device": {
      "ip": "123.123.123.123",
      "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.0.0 Safari/537.36"
    },
    "cookie": "_fbp=fb.1.1653472342558.832801021; some_other=cookie;"
  },
  "integrations": {
    "facebook": {
      "custom_data": {
        "category": "category1"
      },
      "user_data": {
        "fbp": "fb.1.1558571054389.1098115397"
      }
    }
  },
}
```

...into _Facebook CAPI_ events like :

```json
{
  "event_name": "Purchase",
  "event_time": 1707830130,
  "event_source_url": "https://site.com/path?s=2",
  "action_source": "website",
  "user_data": {
    "em": [
      "b4c9a289323b21a01c3e940f150eb9b8c542587f1abfd8f0e1cc1ffc5e475514"
    ],
    "external_id": [
      "user_example_id"
    ],
    "client_ip_address": "123.123.123.123",
    "client_user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.0.0 Safari/537.36",
    "fbc": "fb.1.1554763741205.AbCdEfGhIjKlMnOpQrStUvWxYz1234567890",
    "fbp": "fb.1.1558571054389.1098115397"
  },
  "custom_data": {
    "id": "purchase_id_1234",
    "currency": "EUR",
    "value": 246.9,
    "contents": [
      {
        "id": "product123",
        "quantity": 2,
        "item_price": 123.45
      }
    ]
  }
}
```

The following mappings are fully automated and do not require any additional configuration by default. You can still customize each as follows.

### Mapping: (root)

{% embed url="https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/server-event" %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Fields</th><th width="381">Commanders Act Default Properties</th><th>Facebook Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>event_id</code> <strong>[2][3]</strong></td><td><code>event_id</code> <strong>[1]</strong></td></tr><tr><td><code>-</code></td><td><code>event_name</code></td><td><code>event_name</code> <strong>[4]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>event_time</code> <strong>[5]</strong></td></tr><tr><td><code>Source URL</code></td><td><code>context.page.url</code></td><td><code>event_source_url</code></td></tr><tr><td><code>Referrer URL</code></td><td><code>context.page.referrer</code></td><td><code>referrer_url</code></td></tr><tr><td><code>-</code></td><td><p><code>Enable App tracking</code></p><p><code>type</code></p></td><td><code>action_source</code> <strong>[6]</strong></td></tr><tr><td><code>-</code></td><td><code>opt_out</code> <strong>[3]</strong></td><td><code>opt_out</code> <strong>[7]</strong></td></tr><tr><td><code>-</code></td><td><code>data_processing_options</code> <strong>[3]</strong></td><td><code>data_processing_options</code> <strong>[7]</strong></td></tr><tr><td><code>-</code></td><td><code>data_processing_options_country</code> <strong>[3]</strong></td><td><code>data_processing_options_country</code> <strong>[7]</strong></td></tr><tr><td><code>-</code></td><td><code>data_processing_options_state</code> <strong>[3]</strong></td><td><code>data_processing_options_state</code> <strong>[7]</strong></td></tr></tbody></table>

{% hint style="info" %}
**1.** Set based on available properties, in the reported order on the left. Default to a random generated value based on the timestamp.\
**2.** In the base path/root of your event.\
**3.** In <mark style="color:blue;">`integrations.facebook`</mark> of your event.\
**4.** See [Mapping: event\_name](facebook-conversions-api.md#mapping-event_name) for more details.\
**5.** If no value is provided the current timestamp is used.\
**6.** See [Mapping: action\_source](facebook-conversions-api.md#mapping-action_source) for more details.\
**7.** See more details following this [LINK](https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/server-event).
{% endhint %}

### Mapping: `event_name`

Facebook Pixel specifies [_Standard Events_](https://developers.facebook.com/docs/facebook-pixel/implementation/conversion-tracking#standard-events) whose semantics correspond to events in the [_Commanders Act Standard_](https://community.commandersact.com/platform-x/developers/tracking/events-reference)

If the destination receives a _Commanders Act Event_ with `event_name` matching the list, it will automatically be sent under the associated _Facebook Standard Event_ name. Otherwise, it will be sent without any transformation

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Commanders Act Events</th><th>Facebook Events</th></tr></thead><tbody><tr><td><code>begin_checkout</code></td><td><code>InitiateCheckout</code></td></tr><tr><td><code>purchase</code></td><td><code>Purchase</code></td></tr><tr><td><code>add_to_cart</code></td><td><code>AddToCart</code></td></tr><tr><td><code>view_item</code></td><td><code>ViewContent</code></td></tr><tr><td><code>view_item_list</code></td><td><code>ViewContent</code></td></tr><tr><td><code>search</code></td><td><code>Search</code></td></tr><tr><td><code>add_payment_info</code></td><td><code>AddPaymentInfo</code></td></tr><tr><td><code>add_to_wishlist</code></td><td><code>AddToWishlist</code></td></tr><tr><td><code>generate_lead</code></td><td><code>Lead</code></td></tr><tr><td><code>page_view</code></td><td><code>PageView</code></td></tr><tr><td><code>sign_up</code></td><td><code>CompleteRegistration</code></td></tr><tr><td><code>contact</code></td><td><code>Contact</code></td></tr><tr><td><code>customize_product</code></td><td><code>CustomizeProduct</code></td></tr><tr><td><code>donate</code></td><td><code>Donate</code></td></tr><tr><td><code>find_location</code></td><td><code>FindLocation</code></td></tr><tr><td><code>schedule</code></td><td><code>Schedule</code></td></tr><tr><td><code>search</code></td><td><code>Search</code></td></tr><tr><td><code>start_trial</code></td><td><code>StartTrial</code></td></tr><tr><td><code>submit_application</code></td><td><code>SubmitApplication</code></td></tr><tr><td><code>subscribe</code></td><td><code>Subscribe</code></td></tr></tbody></table>

Examples:

* If the destinations sees a `add_to_cart` event _(IN the list)_, it will send an `AddToCart` to Facebook CAPI
* If the destinations sees a `custom_name` event _(NOT IN the list)_, it will send an `custom_name` to Facebook CAPI _(no transformation)_

{% hint style="info" %}
**Remark:** You can customise the event\_name using _Properties Transformations_ in Destination settings.
{% endhint %}

### Mapping: `action_source`

{% embed url="https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/server-event" %}

By default, `action_source` will be set to `'website'` (most events relate to online activity).\
`IF` `Enable App tracking` is checked THEN `action_source='app'`

#### Offline conversions specificity:

* `IF` your event has the property `type='offline'`
* `THEN` the _Facebook Event_ will have `action_source='physical_store'`
* `ELSE` the _Facebook Event_ will have `action_source='website'`

Example :

```json
// CommandersAct
{
  "event_name": "purchase",
  "type": "offline",
  // ...
}

// Event sent to Facebook API:
{
  "event_name": "Purchase",
  "action_source": "physical_store"
  "custom_data": { /* */ }
  // ...
}
```

If you need to overwrite this value, you currently can use _Properties Transformation_ to set the `integrations.facebook.action_source`.

### Mapping: `user_data`

{% embed url="https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/customer-information-parameters" %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Field</th><th width="322">Commanders Act Default Properties</th><th>Facebook Properties</th></tr></thead><tbody><tr><td><p><code>External id</code></p><p><code>-</code><br><code>-</code><br><code>-</code><br><code>-</code><br><code>-</code></p></td><td><p><code>user.id</code></p><p><code>user.id_sha256</code><br><code>context.device.sdk_id</code><br><code>user.tcId</code><br><code>user.tcid</code><br><code>user.tc_id</code></p></td><td><code>user_data.external_id</code> <strong>[1]</strong> (hashed)</td></tr><tr><td><code>Hashed Email</code></td><td><code>user.email</code></td><td><code>user_data.em</code> (hashed)</td></tr><tr><td><code>Hashed Phone Number</code></td><td><code>user.phone</code></td><td><code>user_data.ph</code> (hashed)</td></tr><tr><td><code>Hashed Gender</code></td><td><code>user.gender</code></td><td><code>user_data.ge</code> (hashed)</td></tr><tr><td><code>Hashed Birth Date</code></td><td><code>user.birthdate</code></td><td><code>user_data.db</code> (hashed)</td></tr><tr><td><code>Hashed First Name</code></td><td><code>user.firstname</code></td><td><code>user_data.fn</code> (hashed)</td></tr><tr><td><code>Hashed Last Name</code></td><td><code>user.lastname</code></td><td><code>user_data.ln</code> (hashed)</td></tr><tr><td><code>Hashed City</code></td><td><code>user.city</code></td><td><code>user_data.ct</code> (hashed)</td></tr><tr><td><code>Hashed State</code></td><td><code>user.state</code></td><td><code>user_data.st</code> (hashed)</td></tr><tr><td><code>Hashed Postal Code</code></td><td><code>user.zipcode</code></td><td><code>user_data.zp</code> (hashed)</td></tr><tr><td><code>Hashed Country</code></td><td><code>user.country</code></td><td><code>user_data.country</code> (hashed)</td></tr><tr><td><code>IP Address</code></td><td><code>ip</code> <strong>[3][4]</strong></td><td><code>user_data.client_ip_address</code></td></tr><tr><td><code>User Agent</code></td><td><code>user_agent</code> <strong>[3][4]</strong></td><td><code>user_data.client_user_agent</code></td></tr><tr><td><code>-</code></td><td><code>fbc</code> <strong>[2]</strong><br><code>The cookie "_fbc"</code> <strong>[5]</strong></td><td><code>user_data.fbc</code> (Click ID)</td></tr><tr><td><code>-</code></td><td><code>fbp</code> <strong>[2]</strong><br><code>The cookie "_fbp"</code> <strong>[5]</strong></td><td><code>user_data.fbp</code> (Browser ID)</td></tr><tr><td><code>Anon ID</code></td><td><code>advertising_id</code> <strong>[3]</strong></td><td><code>user_data.anon_id</code> <strong>[6]</strong></td></tr><tr><td><code>Mobile advertiser ID</code></td><td><code>advertising_id</code> <strong>[3]</strong></td><td><code>user_data.madid</code> <strong>[6]</strong></td></tr><tr><td><code>Facebook Login Id</code></td><td><code>partners.facebook.fb_login_id</code></td><td><code>user_data.fb_login_id</code> <strong>[7]</strong></td></tr><tr><td><code>-</code></td><td><code>user_data[Property Name]</code> <strong>[8]</strong></td><td><code>user_data[Property Name]</code></td></tr></tbody></table>

{% hint style="info" %}
**1.** Comma-separated string: values in the order provided on the left.\
**2.** In <mark style="color:blue;">`integrations.facebook`</mark> or in the root of your events with the first having priority.\
**3.** In <mark style="color:blue;">`context.device`</mark> of your event.\
**4.** Automatically set if generated by Commanders Act OneTag.\
**5.** Automatically created by the Facebook Pixel client-side tag.\
**6.** Only for app events.\
**7.** The identifier issued by Meta when a person first logs into an instance of an app. This is also known as App-Scoped ID.\
**8.** In <mark style="color:blue;">`integrations.facebook`</mark> of your event.
{% endhint %}

Every property can be overridden using `integrations.facebook.user_data.<property>`

#### Minimal required information <a href="#minimal-required-information" id="minimal-required-information"></a>

Events can only be used if there is enough information to match a user. Facebook expects at least one `user_data` property, but strongly advises sending as many properties as possible.

Here are our conditions to send the events :

* at least 1 of those fields: `em`, `ph`, `external_id`, `fbp`, `fbc`
* at least 3 of the other fields

**Note :** external\_id, fbp, fbc will allow matching event with other events. But to match a user, one of those events shall contain additional information (`em` and `ph` are best suited for matching)

### Mapping: `custom_data`

{% embed url="https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/custom-data" %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
The fields `custom_data.contents` and `custom_data.content_ids` are mutually exclusive, meaning that just one of them can be present following this logic:

* If all these properties are present and set within items: `product.id` , `quantity` , and `product.price` , then `custom_data.contents` is set with all product information.
* otherwise, `custom_data.content_ids` is set with all available `product.id` .
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="232">Smart Mapping Fields</th><th width="414">Commanders Act Default Properties</th><th width="336">Facebook Properties</th></tr></thead><tbody><tr><td><code>Value</code></td><td><code>value</code></td><td><code>custom_data.value</code></td></tr><tr><td><p><code>Currency</code></p><p><code>-</code></p></td><td><p><code>currency</code></p><p><code>items.0.currency</code></p></td><td><code>custom_data.currency</code></td></tr><tr><td><code>Net Revenue</code></td><td><code>partners.facebook.net_revenue</code></td><td><code>custom_data.net_revenue</code></td></tr><tr><td><code>Order ID</code></td><td><code>id</code></td><td><code>custom_data.order_id</code></td></tr><tr><td><code>-</code></td><td><code>search_term</code></td><td><code>custom_data.search_string</code></td></tr><tr><td><code>-</code></td><td><code>items.X.product.id</code></td><td><code>custom_data.contents.X.id</code> <strong>[1]</strong></td></tr><tr><td><code>-</code></td><td><code>items.X.quantity</code></td><td><code>custom_data.contents.X.quantity</code> <strong>[1]</strong></td></tr><tr><td><code>-</code></td><td><code>items.X.product.price</code></td><td><code>custom_data.contents.X.item_price</code> <strong>[1]</strong></td></tr><tr><td><code>-</code></td><td><code>items.0.product.name</code></td><td><code>custom_data.content_name</code></td></tr><tr><td><code>-</code></td><td><code>items.0.product.category_1</code></td><td><code>custom_data.content_category</code></td></tr><tr><td><code>-</code></td><td><code>items.X.product.id</code></td><td><code>custom_data.content_ids</code> <strong>[2]</strong></td></tr><tr><td><p><code>Content Type</code></p><p><code>-</code></p></td><td><p><code>partners.facebook.content_type</code></p><p><code>Content type value</code></p></td><td><code>custom_data.content_type</code> <strong>[3]</strong><br><code>custom_data.fb_content_type</code> <strong>[4]</strong></td></tr><tr><td><code>-</code></td><td><code>status</code></td><td><code>custom_data.status</code></td></tr><tr><td><code>Items</code></td><td><code>items.length</code></td><td><code>custom_data.num_items</code></td></tr><tr><td><code>-</code></td><td><code>Send all your event properties as custom data</code></td><td><code>custom_data[Property Name]</code> <strong>[5]</strong></td></tr><tr><td><code>Additional Custom Data</code></td><td><code>custom_data[Propery Name]</code> <strong>[6]</strong></td><td><code>custom_data[Property Name]</code></td></tr></tbody></table>

{% hint style="info" %}
**1.** Mutually exclusive with `custom_data.content_ids` and set if all the following properties are present and valid: `items.X.product.id` , `items.X.product.price` , `items.x.quantity` .\
**2.** Array containing all product identifiers. Mutually exclusive with `custom_data.contents`.\
**3.** Set when <mark style="color:blue;">`action_source`</mark> is <mark style="color:blue;">`website`</mark> or <mark style="color:blue;">`physical_store`</mark> . Depending on the selected value for <mark style="color:blue;">`Content type value`</mark> , which can be found under <mark style="color:blue;">`Advanced Settings`</mark> , this is either <mark style="color:blue;">`product`</mark> or not set. The Smart Mapping field <mark style="color:blue;">`Content Type`</mark> has priority over <mark style="color:blue;">`Content type value`</mark> .\
**4.** Set when <mark style="color:blue;">`action_source`</mark> is <mark style="color:blue;">`app`</mark> .\
**5.** When <mark style="color:blue;">`Send all your event properties as custom data`</mark> is checked all properties in your event with type "string", "number" and "boolean" will be included in <mark style="color:blue;">`custom_data`</mark> with the same property name.\
**6.** In <mark style="color:blue;">`integrations.facebook`</mark> in your event.
{% endhint %}

#### Default behavior

Facebook specifies rules for [standard properties](https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/custom-data). The rest is completely free.

By default, we fill `custom_data` as follows :

1. We copy all _CommandersAct Event_ properties into `custom_data` (except some context fields like `source_key`)
2. Then we map the standard properties according to the table above (can overwrite 1. values)
3. Finally, we overwrite with `integrations.facebook.custom_data.<property>` if exists

#### Overwrite `custom_data`

Best choice would be to use _Properties Transformation_ to modify your event properties which will be copied into `custom_data`.

But you can override the final value using `integrations.facebook.custom_data.<property>`.

Example :

```
cact('trigger', 'purchase', {
    "currency": "EUR",
    "value": 101,
    "integrations": {
        "facebook": {
            "custom_data": {
                "content_name": "some_custom_name",
                "your_field": "your_value"
            }
        }
    }
});
```

### Mapping: `app_data`

{% embed url="https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/app-data" %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Fields</th><th>Commanders Act Properties</th><th>Facebook Properties</th></tr></thead><tbody><tr><td><code>Advertiser tracking enabled</code></td><td><code>ad_tracking_enabled</code> <strong>[1]</strong></td><td><code>advertiser_tracking_enabled</code> <strong>[*]</strong></td></tr><tr><td><code>Application tracking enabled</code></td><td><code>application_tracking_enabled</code> <strong>[1]</strong></td><td><code>application_tracking_enabled</code> <strong>[*]</strong></td></tr><tr><td><code>Campaign IDs</code></td><td><code>context.campaign.name</code></td><td><code>campaign_ids</code></td></tr><tr><td><code>-</code></td><td><code>install_referrer</code> <strong>[2]</strong></td><td><code>install_referrer</code></td></tr><tr><td><code>-</code></td><td><code>installer_package</code> <strong>[2]</strong></td><td><code>installer_package</code></td></tr><tr><td><code>-</code></td><td><code>url_schemes</code> <strong>[2]</strong></td><td><code>url_schemes</code></td></tr><tr><td><code>-</code></td><td><code>windows_attribution_id</code> <strong>[2]</strong></td><td><code>windows_attribution_id</code></td></tr><tr><td><code>OS type</code></td><td><code>type</code> <strong>[1]</strong></td><td><code>extinfo[0]</code> <strong>[3]</strong></td></tr><tr><td><code>App package name</code></td><td><code>app.namespace</code> <strong>[1]</strong></td><td><code>extinfo[1]</code></td></tr><tr><td><code>App Build</code></td><td><code>app.build</code> <strong>[1]</strong></td><td><code>extinfo[2]</code></td></tr><tr><td><code>App Version</code></td><td><code>app.version</code> <strong>[1]</strong></td><td><code>extinfo[3]</code></td></tr><tr><td><code>OS Version</code></td><td><code>os.version</code> <strong>[1]</strong></td><td><code>extinfo[4]</code></td></tr><tr><td><code>Device Model</code></td><td><code>model</code> <strong>[1]</strong></td><td><code>extinfo[5]</code></td></tr><tr><td><code>Device Language</code></td><td><code>language</code> <strong>[1]</strong></td><td><code>extinfo[6]</code></td></tr><tr><td><code>Device Abbreviated Timezone</code></td><td><code>[No default field]</code> <strong>[4]</strong></td><td><code>extinfo[7]</code></td></tr><tr><td><code>Network Carrier</code></td><td><code>network.carrier</code> <strong>[1]</strong></td><td><code>extinfo[8]</code></td></tr><tr><td><code>Screen Width</code></td><td><code>screen.width</code> <strong>[1]</strong></td><td><code>extinfo[9]</code></td></tr><tr><td><code>Screen Height</code></td><td><code>screen.height</code> <strong>[1]</strong></td><td><code>extinfo[10]</code></td></tr><tr><td><code>Screen Density</code></td><td><code>screen.density</code> <strong>[1]</strong></td><td><code>extinfo[11]</code></td></tr><tr><td><code>CPU Cores</code></td><td><code>[No default field]</code> <strong>[5]</strong></td><td><code>extinfo[12]</code></td></tr><tr><td><code>External Storage Size</code></td><td><code>[No default field]</code> <strong>[6]</strong></td><td><code>extinfo[13]</code></td></tr><tr><td><code>Available Storage Size</code></td><td><code>[No default field]</code> <strong>[7]</strong></td><td><code>extinfo[14]</code></td></tr><tr><td><code>Device Timezone</code></td><td><code>timezone</code> <strong>[1]</strong></td><td><code>extinfo[15]</code></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** In <mark style="color:blue;">`context.device`</mark> of your event.\
**2.** In <mark style="color:blue;">`integrations.facebook`</mark> or in the root of your events with the first having priority.\
**3.** When <mark style="color:blue;">`context.device.type`</mark> is set with <mark style="color:blue;">`Android`</mark> or <mark style="color:blue;">`iOS`</mark> (case insensitive), this is set with <mark style="color:blue;">`a2`</mark> or <mark style="color:blue;">`i`</mark>`2` respectively.\
**4.** Can be set in <mark style="color:blue;">`Smart Mapping`</mark> → <mark style="color:blue;">`App Data`</mark> → <mark style="color:blue;">`Device Abbreviated Timezone`</mark> .\
**5.** Can be set in <mark style="color:blue;">`Smart Mapping`</mark> → <mark style="color:blue;">`App Data`</mark> → <mark style="color:blue;">`CPU Cores`</mark> .\
**6.** Can be set in <mark style="color:blue;">`Smart Mapping`</mark> → <mark style="color:blue;">`App Data`</mark> → <mark style="color:blue;">`External Storage Size`</mark> .\
**7.** Can be set in <mark style="color:blue;">`Smart Mapping`</mark> → <mark style="color:blue;">`App Data`</mark> → <mark style="color:blue;">`Available Storage Size`</mark> .
{% endhint %}

### `integrations.facebook.*` deprecation

{% hint style="warning" %}
`integrations.facebook.*` usage will be deprecated.\
The feature is still working, but it is recommended to use the destination settings instead for maintenance and reliability purpose.
{% endhint %}

## Check results on Facebook interface

To view quality matching on Facebook interface, go here:\
**Events manager** **>** **select the event > View Details > Event Matching > Rating Background**

## How to send offline conversions

The recommanded way is to use the [HTTP Tracking API](../../../sources/sources-catalog/http-tracking-api.md) source to send your offline events from your servers (or any other emmiter).\
You just need to send a [purchase event](../../../../developers/tracking/events-reference/#purchase) with the `type` property equals to `offline`\
More details on the automatic mapping here: [Mapping action\_source](facebook-conversions-api.md#offline-conversions-specificity)
