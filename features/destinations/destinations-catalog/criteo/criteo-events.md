---
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
---

# Criteo - Events

[Criteo ](https://www.criteo.com/)is an advertising company that provides online display advertisements.\
Using the [Criteo Server-side API](https://guides.criteotilt.com/onetag/s2s/#sending-events) you can track web events you are used to report via [Criteo OneTag client-side JS (pixel)](https://help.criteo.com/kb/guide/en/all-criteo-onetag-events-and-parameters-vZbzbEeY86/Steps/775825). This is normally required for technical and legal reasons.

## Key features

The Criteo - Events destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Criteo's events](https://help.criteo.com/kb/guide/en/all-criteo-onetag-events-and-parameters-vZbzbEeY86/Steps/775825), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional information based on your specific needs (E.g. adding custom events, custom event and user properties).
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is brought to Criteo.

## Destination setup

{% hint style="danger" %}
**The** [**Criteo salted user ID (GUM ID)**](https://guides.criteotilt.com/onetag/s2s/#criteo-gum-call) **is required**: this value must be passed to this destination by including the cookie <mark style="color:blue;">**`crto_mapped_user_id`**</mark>.\
The easiest way to manage this cookie is to **use this client-side tags in our tag library :&#x20;**<mark style="color:blue;">**Criteo - User Identification**</mark> in your web container.
{% endhint %}

### Configuration

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Account Id</code></td><td><em><strong><code>Required</code></strong></em><br>The retailer’s Criteo <a href="https://marketing.criteo.com/">Account Id</a> can be found in the <a href="https://marketing.criteo.com/">Management Center</a>.</td></tr><tr><td><code>Caller Id</code></td><td>The Caller Id is used for identifying the user and it's provided by Criteo upon request.</td></tr></tbody></table>

## Quick reference

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Commanders Act Events</th><th>Criteo Events</th></tr></thead><tbody><tr><td><code>add_payment_info</code></td><td><code>addPaymentInfo</code></td></tr><tr><td><code>add_to_cart</code></td><td><code>addToCart</code></td></tr><tr><td><code>begin_checkout</code></td><td><code>beginCheckout</code></td></tr><tr><td><code>login</code></td><td><code>login</code></td></tr><tr><td><code>page_view</code></td><td><code>viewHome</code> and/or<br><code>viewPage</code> <strong>[1]</strong></td></tr><tr><td><code>purchase</code></td><td><code>trackTransaction</code></td></tr><tr><td><code>search</code><br><code>view_item_list</code></td><td><code>viewList</code></td></tr><tr><td><code>view_cart</code></td><td><code>viewBasket</code></td></tr><tr><td><code>view_item</code></td><td><code>viewItem</code></td></tr></tbody></table>

{% hint style="info" %}
**1.** If <mark style="color:blue;">`page.type`</mark> is <mark style="color:blue;">`home`</mark> then <mark style="color:blue;">`viewHome`</mark> is also sent with <mark style="color:blue;">`viewPage`</mark>, otherwise, just <mark style="color:blue;">`viewPage`</mark> is forwarded.
{% endhint %}

## Field mappings

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Commanders Act Properties</th><th>Criteo Properties</th></tr></thead><tbody><tr><td><code>event_timestamp</code></td><td><code>timestamp</code> <strong>[1]</strong></td></tr><tr><td><code>Account Id</code></td><td><code>account</code></td></tr><tr><td><code>device.ip</code></td><td><code>ip</code></td></tr><tr><td><code>page.location.href</code></td><td><code>full_url</code></td></tr><tr><td><code>page.referrer</code></td><td><code>previous_url</code></td></tr><tr><td><code>(app.name)</code></td><td><code>site_type</code> <strong>[2]</strong></td></tr><tr><td><code>device.user_agent</code></td><td><code>useragent</code></td></tr><tr><td><code>user.id</code></td><td><code>retailer_visitor_id</code></td></tr><tr><td><code>Caller Id</code></td><td><code>id.mapping_key</code></td></tr><tr><td><code>user.email</code></td><td><code>id.email.raw</code></td></tr><tr><td><code>user.email_md5</code></td><td><p><code>id.email.md5</code> and</p><p><code>id.email.sha256_md5</code> <strong>[3]</strong></p></td></tr><tr><td><code>user.email_sha256</code></td><td><code>id.email.sha256</code></td></tr></tbody></table>

{% hint style="info" %}
**1.** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601).\
**2.** This is either <mark style="color:blue;">`m`</mark> or <mark style="color:blue;">`d`</mark>, depending if <mark style="color:blue;">`app.name`</mark> is defined or not.\
**3.** <mark style="color:blue;">`id.email.sha256_md5`</mark> is automatically hashed.
{% endhint %}
