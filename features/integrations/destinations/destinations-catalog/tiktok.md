# TikTok

TikTok is a social platform short-form video hosting service.\
The TikTok Events API is a server-side integration that allows you to share website and app visitor events directly with TikTok using [Events API for Web](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890979375106) and [Events API for App](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890978528258).

{% hint style="info" %}
The [Events API for App](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890978528258) support is currently under beta testing and coming soon.
{% endhint %}

## Key features

The TikTok destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [TikTok's one](https://ads.tiktok.com/marketing\_api/docs?rid=959icq5stjr\&id=1701890977725441), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Snapchat.
* **Support for test event code**: real-time validation in your test environments with field `test_event_code`.

## Destination setup

Before you get started with this destination, make sure you can access the [TikTok Ads Manager](https://ads.tiktok.com).

### Configuration

| Settings        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Access Token    | <p><em><strong><code>Required</code> </strong></em> for <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">WEB events</a>.</p><p>Your <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-How%20to%20generate%20an%20access%20token">API Access Token</a> as provided by TikTok. More details are available by following this <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-How%20to%20generate%20an%20access%20token">LINK</a>.</p>                      |
| TikTok Pixel ID | <p><em><strong><code>Required</code></strong></em> for <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">WEB events</a>.</p><p>Your <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-Where%20to%20Find%20pixel_code">Pixel ID</a> as provided by TikTok. You can only add a single pixel id per destination. More details are available by following this <a href="https://ads.tiktok.com/gateway/docs/index?identify_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48&#x26;language=ENGLISH&#x26;doc_id=1727537566862337#item-link-Where%20to%20Find%20pixel_code">LINK</a>.</p> |
| Test Event Code | <p>For <a href="https://ads.tiktok.com/marketing_api/docs?id=1727541103358977">Web events</a> only.</p><p>This is used to test event tracking before deploying in production. This code can be found in the <mark style="color:blue;">TikTok Ads Manager</mark> following <code>Assets</code> ➜ <code>Events</code> ➜ <code>Manage (Web Events)</code> ➜ Select your pixel ➜ <code>Test Events (Tab)</code>.</p>                                                                                                                                                                                                                                                                                                                                                         |

## Quick reference

### Web events

{% hint style="info" %}
TikTok supported web events are detailed in this [LINK](https://ads.tiktok.com/marketing\_api/docs?id=1727541103358977).
{% endhint %}

| Commanders Act Events | TikTok Events          |
| --------------------- | ---------------------- |
| `add_payment_info`    | `AddPaymentInfo`       |
| `add_to_cart`         | `AddToCart`            |
| `add_to_wishlist`     | `AddToWishlist`        |
| `begin_checkout`      | `InitiateCheckout`     |
| `click_button`        | `ClickButton`          |
| `complete_payment`    | `CompletePayment`      |
| `contact`             | `Contact`              |
| `download`            | `Download`             |
| `page_view`           | `ViewContent`          |
| `purchase`            | `PlaceAnOrder`         |
| `search`              | `Search`               |
| `sign_up`             | `CompleteRegistration` |
| `submit_form`         | `SubmitForm`           |
| `subscribe`           | `Subscribe`            |

## Field Mappings

{% hint style="info" %}
If you also use TikTok client-side pixel, this automatically saves a unique identifier in the [\_ttp ](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Context%20object%20parameters)cookie which is used to match website visitor events with TikTok ads. This destination sets the field<mark style="color:blue;">`context.user.ttp`</mark>using the value provided in the cookie. This is a recommended step.\
[Tiktok Click ID](https://ads.tiktok.com/marketing\_api/docs?rid=4eezrhr6lg4\&id=1701890980108353) or [ttclid ](https://ads.tiktok.com/marketing\_api/docs?rid=4eezrhr6lg4\&id=1701890980108353)is a tracking parameters that is attached to your ad's landing page URLs. This destination retrieves the ttclid by looking for the <mark style="color:blue;">ttclid</mark> cookie and its value. If no cookie is found then it tries to get a value from the field<mark style="color:blue;">`page.location.href`</mark>which is then bridged to the field<mark style="color:blue;">`context.ad.callback`</mark>.
{% endhint %}

| Commanders Act Properties          | TikTok Properties                             |
| ---------------------------------- | --------------------------------------------- |
| `event_timestamp`                  | `timestamp` **\[1]**                          |
| `properties.id`                    | `event_id` **\[2]**                           |
| `TikTok Pixel ID`                  | `pixel_code`                                  |
| `page.url`                         | `context.page.url`                            |
| `page.referrer`                    | `context.page.referrer`                       |
| `device.ip`                        | `context.ip`                                  |
| `device.user_agent`                | `context.user_agent`                          |
| `Test Event Code`                  | `test_event_code`                             |
| `properties.user.id`               | `context.user.external_id` **\[3]**           |
| `properties.user.email`            | `context.user.email` **\[3]**                 |
| `properties.user.phone`            | `context.user.phone_number` **\[3]**          |
| `properties.items.X.content_type`  | `properties.contents.X.content_type` **\[4]** |
| `properties.items.X.id`            | `properties.contents.X.content_id`            |
| `properties.items.X.product.price` | `properties.contents.X.price`                 |
| `properties.items.X.quantity`      | `properties.contents.X.quantity`              |
| `properties.currency`              | `properties.currency`                         |
| `event_name`                       | `properties.description`                      |
| `properties.search_term`           | `properties.query`                            |
| `properties.value`                 | `properties.value`                            |

{% hint style="info" %}
**\[1]** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[2]** This is required if you are sending overlapping events from both TikTok client-side pixel and this destination. More details on the deduplication are available following this [LINK](https://ads.tiktok.com/marketing\_api/docs?rid=p41a33fdhon\&id=1723170195197953).\
**\[3]** Field automatically hashed if set with sensitive clear data.\
**\[4]** This is either[`product`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters)or[`product_group`](https://ads.tiktok.com/gateway/docs/index?identify\_key=2b9b4278e47b275f36e7c39a4af4ba067d088e031d5f5fe45d381559ac89ba48\&language=ENGLISH\&doc\_id=1727541103358977#item-link-Properties%20object%20parameters)depending on how you have configured your data feed when you set up your product catalog.
{% endhint %}
