# TikTok Events API

[TikTok for Business](https://www.tiktok.com/business/en) is a global platform designed to give brands and marketers the solutions to be creative storytellers and meaningfully engage with the TikTok community.\
The TikTok Events API is a server-side integration that allows you to share website and app visitor events directly with TikTok using their [Events API for Web](https://ads.tiktok.com/marketing\_api/docs?id=1739584809311234) and [Events API for App](https://ads.tiktok.com/marketing\_api/docs?id=1739584805049345) version 1.3.

{% hint style="info" %}
The [Events API for App](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890978528258) support is currently under beta testing and coming soon.
{% endhint %}

## Key features

The TikTok Events API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) matches [TikTok's one](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890977725441), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to TikTok.
* **Support for test event code**: real-time validation in your test environments with field `test_event_code`.

## Destination setup

Before you get started with this destination, make sure you can access [TikTok Ads Manager](https://ads.tiktok.com).

{% hint style="info" %}
TikTok doesn't support custom event and/or additional property in the payload.\
In case these are still sent, TikTok will fully discard the associated event and its data.
{% endhint %}

### Configuration

| Settings          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Access Token`    | <p><em><strong><code>Required</code></strong></em> for <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">WEB events</a>. <br>Your <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-How%20to%20generate%20an%20access%20token">API Access Token</a> as provided by TikTok. More details are available by following this <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-How%20to%20generate%20an%20access%20token">LINK</a>.</p>                       |
| `TikTok Pixel ID` | <p><em><strong><code>Required</code></strong></em> for <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">WEB events</a>. <br>Your <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-Where%20to%20Find%20pixel_code">Pixel ID</a> as provided by TikTok. You can only add a single pixel id per destination. More details are available by following this <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-Where%20to%20Find%20pixel_code">LINK</a>.</p> |
| `Test Event Code` | For [Web events](https://ads.tiktok.com/marketing\_api/docs?id=1727541103358977) only. This is used to test event tracking before deploying in production. This code can be found in the [TikTok Ads Manager](https://ads.tiktok.com/) following `Assets` ➜ `Events` ➜ `Manage (Web Events)` ➜ Select your pixel ➜ `Test Events (Tab)` **\[1]**                                                                                                                                                                                                                                                                                                                                                                                                                        |



{% hint style="info" %}
**\[1]** The <mark style="color:blue;">`Test Event Code`</mark> can only be set in test environments as TikTok won't save data coming from live events where this code is included. More details are available following this [LINK](https://ads.tiktok.com/marketing\_api/docs?id=1724255493685249).
{% endhint %}

## Quick reference

### Web events

{% hint style="info" %}
TikTok supported web events are detailed in this [LINK](https://ads.tiktok.com/marketing\_api/docs?id=1727541103358977).
{% endhint %}

| Commanders Act Events                                            | TikTok Events              |
| ---------------------------------------------------------------- | -------------------------- |
| `add_payment_info`                                               | `AddPaymentInfo`           |
| `add_to_cart`                                                    | `AddToCart`                |
| `add_to_wishlist`                                                | `AddToWishlist`            |
| `begin_checkout`                                                 | `InitiateCheckout`         |
| `click_button`                                                   | `ClickButton`              |
| <p><code>complete_payment</code></p><p><code>purchase</code></p> | `CompletePayment` **\[1]** |
| `contact`                                                        | `Contact`                  |
| `download`                                                       | `Download`                 |
| `page_view`                                                      | `ViewContent`              |
| `search`                                                         | `Search`                   |
| `sign_up`                                                        | `CompleteRegistration`     |
| `submit_form`                                                    | `SubmitForm`               |
| `subscribe`                                                      | `Subscribe`                |

{% hint style="info" %}
**\[1]** With <mark style="color:blue;">`CompletePayment`</mark> events you can take advantage of TikTok [Value-Based Optimization for Web](https://ads.tiktok.com/help/article?aid=10008856) (VBO Web).
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
TikTok client-side pixel saves a unique identifier in cookie [**\_ttp**](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters)**,** which is used to match website visitor events with TikTok ads. This destination starts by getting this identifier from <mark style="color:blue;">`partners.tiktok.ttp`</mark> . If it's not present, it looks for the previously mentioned cookie [**\_ttp**](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters) and sets TikTok <mark style="color:blue;">`context.user.ttp`</mark> with the resulting value.\
The [Tiktok Click ID](https://ads.tiktok.com/marketing\_api/docs?rid=4eezrhr6lg4\&id=1701890980108353), also known as [ttclid](https://ads.tiktok.com/marketing\_api/docs?rid=4eezrhr6lg4\&id=1701890980108353), is a tracking parameter that is attached to your ad's landing page URLs. This destination checks if <mark style="color:blue;">`partners.tiktok.ttclid`</mark> is set with the ttclid value. If it's not present, it looks for cookie <mark style="color:blue;">ttclid</mark>. If none is found it tries by parsing the value from <mark style="color:blue;">`page.location.href`</mark> .\
[Advanced matching](https://ads.tiktok.com/marketing\_api/docs?id=1701890972946433) parameters are highly recommended to improve attribution rates: ensure <mark style="color:blue;">`properties.user.email`</mark> and/or <mark style="color:blue;">`properties.user.phone`</mark> is set. More details on the phone number format rules are available following this [LINK](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters).
{% endhint %}

<table><thead><tr><th width="330.6685580062746">Commanders Act Properties</th><th>TikTok Properties</th></tr></thead><tbody><tr><td><code>context.event_timestamp</code></td><td><code>timestamp</code> <strong>[1]</strong></td></tr><tr><td><code>id</code></td><td><code>event_id</code> <strong>[2]</strong></td></tr><tr><td><code>TikTok Pixel ID</code></td><td><code>pixel_code</code></td></tr><tr><td><code>Test Event Code</code></td><td><code>test_event_code</code></td></tr><tr><td><code>context.page.url</code></td><td><code>context.page.url</code></td></tr><tr><td><code>context.page.referrer</code></td><td><code>context.page.referrer</code></td></tr><tr><td><code>context.device.ip</code></td><td><code>context.ip</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>context.user_agent</code></td></tr><tr><td><code>user.id</code></td><td><code>context.user.external_id</code> <strong>[3]</strong></td></tr><tr><td><code>user.email</code></td><td><code>context.user.email</code> <strong>[3]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>context.user.phone_number</code> <strong>[3]</strong></td></tr><tr><td><code>items.X.content_type</code></td><td><code>properties.contents.X.content_type</code> <strong>[4]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>properties.contents.X.content_id</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>properties.contents.X.price</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>properties.contents.X.quantity</code></td></tr><tr><td><code>items.X.product.category_1</code></td><td><code>properties.contents.X.content_category</code></td></tr><tr><td><code>items.X.product.name</code></td><td><code>properties.contents.X.content_name</code></td></tr><tr><td><code>content_type</code></td><td><code>properties.content_type</code> <strong>[4]</strong></td></tr><tr><td><code>currency</code></td><td><code>properties.currency</code></td></tr><tr><td><code>event_name</code></td><td><code>properties.description</code></td></tr><tr><td><code>search_term</code></td><td><code>properties.query</code></td></tr><tr><td><code>value</code></td><td><code>properties.value</code></td></tr><tr><td><code>status</code></td><td><code>properties.status</code></td></tr><tr><td><code>partners.tiktok.ttp</code></td><td><code>context.user.ttp</code> <strong>[5]</strong></td></tr><tr><td><code>partners.tiktok.ttclid</code></td><td><code>context.ad.callback</code> <strong>[6]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[2]** This is required if you are sending overlapping events from both TikTok client-side pixel and this destination. More details on the deduplication are available following this [LINK](https://ads.tiktok.com/marketing\_api/docs?rid=p41a33fdhon\&id=1723170195197953).\
**\[3]** Field automatically hashed with SHA256 if passed in clear.\
**\[4]** This is either[`product`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters)or[`product_group`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters)depending on how you have configured your data feed when you set up your product catalog. Default value:[`product`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters).\
**\[5]** <mark style="color:blue;">`partners.tiktok.ttp`</mark> has priority over cookie <mark style="color:blue;">**\_ttp**</mark>.\
**\[6]** <mark style="color:blue;">`partners.tiktok.ttclid`</mark> has priority over cookie <mark style="color:blue;">**ttclid**</mark>. and <mark style="color:blue;">`page.location.href`</mark> parsing.
{% endhint %}
