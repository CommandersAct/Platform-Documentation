# TikTok

[TikTok ](https://www.tiktok.com)is a social platform short-form video hosting service.\
The TikTok Events API is a server-side integration that allows you to share website and app visitor events directly with TikTok using their [Events API for Web](https://ads.tiktok.com/marketing\_api/docs?id=1739584809311234) and [Events API for App](https://ads.tiktok.com/marketing\_api/docs?id=1739584805049345) version 1.3.

{% hint style="info" %}
The [Events API for App](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890978528258) support is currently under beta testing and coming soon.
{% endhint %}

## Key features

The TikTok destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) matches [TikTok's one](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890977725441), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to TikTok.
* **Support for test event code**: real-time validation in your test environments with field `test_event_code`.

## Destination setup

Before you get started with this destination, make sure you can access [TikTok Ads Manager](https://ads.tiktok.com).

{% hint style="info" %}
TikTok doesn't support custom event and/or additional property in the payload.\
In case these are still sent, TikTok will fully discard the associated event and its data.
{% endhint %}

### Configuration

| Settings           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Access Token`     | <p><em><strong><code>Required</code> </strong></em> for <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">WEB events</a>.</p><p>Your <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-How%20to%20generate%20an%20access%20token">API Access Token</a> as provided by TikTok. More details are available by following this <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-How%20to%20generate%20an%20access%20token">LINK</a>.</p>                      |
| `TikTok Pixel ID`  | <p><em><strong><code>Required</code></strong></em> for <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">WEB events</a>.</p><p>Your <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-Where%20to%20Find%20pixel_code">Pixel ID</a> as provided by TikTok. You can only add a single pixel id per destination. More details are available by following this <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-Where%20to%20Find%20pixel_code">LINK</a>.</p> |
| `Test Event Code`  | <p>For <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">Web events</a> only.</p><p>This is used to test event tracking before deploying in production. This code can be found in the <a href="https://ads.tiktok.com/">TikTok Ads Manager</a> following <code>Assets</code> ➜ <code>Events</code> ➜ <code>Manage (Web Events)</code> ➜ Select your pixel ➜ <code>Test Events (Tab)</code>.</p>                                                                                                                                                                                                                                                                                                                                                    |
| `User Identifier`  | You can bridge your selected user identifier for logged users.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `User Email Field` | Select a standard property for TikTok `context.user.email` field. This can be either `User Email` **\[1]**, `User Email MD5` **\[1]** or `User Email Sha256`. More details are available following this [LINK](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters).                                                                                                                                                                                                                                                                                                                                            |

{% hint style="info" %}
**\[1]** Hashed with SHA256.\
The<mark style="color:blue;">`Test Event Code`</mark>can only be set in test environments as TikTok won't save data coming from live events where this code is included. More details are available following this [LINK](https://ads.tiktok.com/marketing\_api/docs?id=1724255493685249).
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
**\[1]** With<mark style="color:blue;">`CompletePayment`</mark>events you can take advantage of TikTok [Value-Based Optimization for Web](https://ads.tiktok.com/help/article?aid=10008856) (VBO Web).
{% endhint %}

## Field Mappings

{% hint style="info" %}
TikTok client-side pixel saves a unique identifier in cookie [**\_ttp**](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters)**,** which is used to match website visitor events with TikTok ads. This destination starts by getting this identifier from Commanders Act<mark style="color:blue;">`partners.tiktok.ttp`</mark>property. If it's not present, it looks for the previously mentioned cookie [**\_ttp**](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters) **** and sets TikTok<mark style="color:blue;">`context.user.ttp`</mark>property with the resulting value.\
The [Tiktok Click ID](https://ads.tiktok.com/marketing\_api/docs?rid=4eezrhr6lg4\&id=1701890980108353), also known as [ttclid](https://ads.tiktok.com/marketing\_api/docs?rid=4eezrhr6lg4\&id=1701890980108353), is a tracking parameter that is attached to your ad's landing page URLs. This destination checks if<mark style="color:blue;">`partners.tiktok.ttclid`</mark>is set with the ttclid value. If it's not present, it looks for cookie <mark style="color:blue;">ttclid</mark>. If none is found it tries by parsing the value from<mark style="color:blue;">`page.location.href`</mark>.\
[Advanced matching](https://ads.tiktok.com/marketing\_api/docs?id=1701890972946433) parameters are highly recommended to improve attribution rates: ensure<mark style="color:blue;">`properties.user.email`</mark>and/or<mark style="color:blue;">`properties.user.phone`</mark>is <mark style="color:blue;"></mark> set. More details on the phone number format rules are available following this [LINK](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters).
{% endhint %}

| Commanders Act Properties                                                                                                              | TikTok Properties                             |
| -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| `event_timestamp`                                                                                                                      | `timestamp` **\[1]**                          |
| `properties.id`                                                                                                                        | `event_id` **\[2]**                           |
| `TikTok Pixel ID`                                                                                                                      | `pixel_code`                                  |
| `Test Event Code`                                                                                                                      | `test_event_code`                             |
| `page.url`                                                                                                                             | `context.page.url`                            |
| `page.referrer`                                                                                                                        | `context.page.referrer`                       |
| `device.ip`                                                                                                                            | `context.ip`                                  |
| `device.user_agent`                                                                                                                    | `context.user_agent`                          |
| `properties.user.id`                                                                                                                   | `context.user.external_id` **\[3]**           |
| <p><code>properties.user.email</code></p><p><code>properties.user.email_md5</code></p><p><code>properties.user.email_sha256</code></p> | `context.user.email` **\[3]**                 |
| `properties.user.phone`                                                                                                                | `context.user.phone_number` **\[3]**          |
| `properties.items.X.content_type`                                                                                                      | `properties.contents.X.content_type` **\[4]** |
| `properties.items.X.id`                                                                                                                | `properties.contents.X.content_id`            |
| `properties.items.X.product.price`                                                                                                     | `properties.contents.X.price`                 |
| `properties.items.X.quantity`                                                                                                          | `properties.contents.X.quantity`              |
| `properties.content_type`                                                                                                              | `properties.content_type` **\[4]**            |
| `properties.currency`                                                                                                                  | `properties.currency`                         |
| `event_name`                                                                                                                           | `properties.description`                      |
| `properties.search_term`                                                                                                               | `properties.query`                            |
| `properties.value`                                                                                                                     | `properties.value`                            |
| `partners.tiktok.ttp`                                                                                                                  | `context.user.ttp` **\[5]**                   |
| `partners.tiktok.ttclid`                                                                                                               | `context.ad.callback` **\[6]**                |

{% hint style="info" %}
**\[1]** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[2]** This is required if you are sending overlapping events from both TikTok client-side pixel and this destination. More details on the deduplication are available following this [LINK](https://ads.tiktok.com/marketing\_api/docs?rid=p41a33fdhon\&id=1723170195197953).\
**\[3]** Field automatically hashed with SHA256 if not passed using this algorithm.\
**\[4]** This is either[`product`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters)or[`product_group`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters)depending on how you have configured your data feed when you set up your product catalog. Default value:[`product`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters).\
**\[5]**<mark style="color:blue;">`partners.tiktok.ttp`</mark>has priority over cookie <mark style="color:blue;">**\_ttp**</mark>.\
**\[6]**<mark style="color:blue;">`partners.tiktok.ttclid`</mark>has priority over cookie <mark style="color:blue;">**ttclid**</mark>. <mark style="color:blue;">****</mark> and<mark style="color:blue;">`page.location.href`</mark>parsing.
{% endhint %}
