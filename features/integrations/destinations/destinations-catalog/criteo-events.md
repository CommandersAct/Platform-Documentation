# Criteo (events)

Criteo is an advertising company that provides online display advertisements.\
Using the [Criteo Server-side API](https://guides.criteotilt.com/onetag/s2s/#sending-events) you can track those web events you are used to report via [Criteo OneTag client-side JS (pixel)](https://help.criteo.com/kb/guide/en/all-criteo-onetag-events-and-parameters-vZbzbEeY86/Steps/775825) - This is normally required for technical and legal reasons.

## Key features

The Criteo (events) destination provides the following key features:

* **Events structure**: our [Event reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model suits [Criteo's events](https://help.criteo.com/kb/guide/en/all-criteo-onetag-events-and-parameters-vZbzbEeY86/Steps/775825), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional information based on your specific needs (E.g. adding custom events, custom event and user properties).
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is brought to Criteo.

## Destination setup

{% hint style="info" %}
When available, the [Criteo salted user ID (GUM ID)](https://guides.criteotilt.com/onetag/s2s/#criteo-gum-call) is required.\
This is retrieved by getting the value of the cookie<mark style="color:blue;">**`crto_mapped_user_id`**</mark>and can be set using the <mark style="color:blue;">Criteo - User Identification</mark> client-side template which is available in our library following these steps:`INTEGRATION` ➜ `Sources`➜ `Web Containers`.
{% endhint %}

### Configuration

| Settings     | Description                                                                                                                                                                                                                  |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Account Id` | <p><em><strong><code>Required</code></strong></em></p><p>The retailer’s Criteo <a href="https://marketing.criteo.com/">Account Id</a> can be found in the <a href="https://marketing.criteo.com/">Management Center</a>.</p> |
| `Caller Id`  | The Caller Id is used for identifying the user and it's provided by Criteo upon request.                                                                                                                                     |

## Quick reference

| Commanders Act Events | Criteo Events                                                                     |
| --------------------- | --------------------------------------------------------------------------------- |
| `add_payment_info`    | `addPaymentInfo`                                                                  |
| `add_to_cart`         | `addToCart`                                                                       |
| `begin_checkout`      | `beginCheckout`                                                                   |
| `login`               | `login`                                                                           |
| `page_view`           | <p><code>viewHome</code> and/or<br><code>viewPage</code> <strong>[1]</strong></p> |
| `purchase`            | `trackTransaction`                                                                |
| `search`              | `viewList`                                                                        |
| `view_cart`           | `viewBasket`                                                                      |
| `view_item`           | `viewItem`                                                                        |

{% hint style="info" %}
**\[1]** If<mark style="color:blue;">`properties.page.type`</mark>is<mark style="color:blue;">`home`</mark>then<mark style="color:blue;">`viewHome`</mark>is also sent with<mark style="color:blue;">`viewPage`</mark>, otherwise, just<mark style="color:blue;">`viewPage`</mark>is forwarded. ``&#x20;
{% endhint %}

## Field Mappings

| Commanders Act Properties      | Criteo Properties                                                                                |
| ------------------------------ | ------------------------------------------------------------------------------------------------ |
| `event_timestamp`              | `timestamp` **\[1]**                                                                             |
| `Account Id`                   | `account`                                                                                        |
| `device.ip`                    | `ip`                                                                                             |
| `page.location.href`           | `full_url`                                                                                       |
| `page.referrer`                | `previous_url`                                                                                   |
| `(app.name)`                   | `site_type` **\[2]**                                                                             |
| `device.user_agent`            | `useragent`                                                                                      |
| `properties.user.id`           | `retailer_visitor_id`                                                                            |
| `Caller Id`                    | `id.mapping_key`                                                                                 |
| `properties.user.email`        | `id.email.raw`                                                                                   |
| `properties.user.email_md5`    | <p><code>id.email.md5</code> and</p><p><code>id.email.sha256_md5</code> <strong>[3]</strong></p> |
| `properties.user.email_sha256` | `id.email.sha256`                                                                                |

{% hint style="info" %}
**\[1]** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[2]** If<mark style="color:blue;">`app.name`</mark>is defined then this field is set with<mark style="color:blue;">`m`</mark>, otherwise,<mark style="color:blue;">`d`</mark>.\
``**\[3]**<mark style="color:blue;">`id.email.sha256_md5`</mark>is automatically hashed.
{% endhint %}
