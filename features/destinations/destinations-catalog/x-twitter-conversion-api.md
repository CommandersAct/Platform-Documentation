---
description: X CAPI, Twitter CAPI
---

# X (Twitter) Conversion API

[X](https://twitter.com), also referred to by its former name [Twitter](https://twitter.com), is a social media website.\
Using this destination you can share conversion data with X to enable the measurement of campaigns through [Conversion API](https://developer.twitter.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api).

## Key features

The X Conversion API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [X conversion events](https://developer.x.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

Before using this destination, you need to create a new conversion event in [Ads Manager](https://ads.twitter.com) or use an existing event already created and used with the [Twitter Pixel](https://business.twitter.com/en/help/campaign-measurement-and-analytics/conversion-tracking-for-websites.html).

{% hint style="info" %}
To create a conversion event, access [Ads Manager](https://ads.twitter.com) and navigate to <mark style="color:blue;">`Tools`</mark> `(1)` → <mark style="color:blue;">`Events manager`</mark> `(2)` :

![](../../../.gitbook/assets/twitter\_1.png)

&#x20;If you do not have a Twitter Pixel event source, create it by selecting <mark style="color:blue;">`Add event source`</mark> `(3)` :

![](../../../.gitbook/assets/twitter\_2.png)\
The resulting identifier is your <mark style="color:blue;">`Pixel Id`</mark> : See [Configuration](x-twitter-conversion-api.md#configuration) for more details.\
Now you can create an event by clicking <mark style="color:blue;">`Add events`</mark> `(4)` :

![](../../../.gitbook/assets/twitter\_3.png)\
The resulting identifier is you <mark style="color:blue;">`Event Id`</mark> : See [Configuration](x-twitter-conversion-api.md#configuration) for more details.\
If you want to use an existing event that you're already using with the Twitter pixel, you can do so by getting its <mark style="color:blue;">`Event Id`</mark> from the event list in the "Overview" tab.
{% endhint %}

{% hint style="info" %}
X Conversion API supports deduplication with your client-side [Twitter Pixel](https://business.twitter.com/en/help/campaign-measurement-and-analytics/conversion-tracking-for-websites.html).\
Check the "Smart Mapping" field <mark style="color:blue;">`Transaction Id`</mark> , [Field Mappings](x-twitter-conversion-api.md#field-mappings) (See property <mark style="color:blue;">`conversion_id`</mark> ) or this [LINK ](https://developer.twitter.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api)for more details (See section "Duplication between Pixel and Conversion API").&#x20;
{% endhint %}

### Configuration

<table><thead><tr><th width="349">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><em><strong><code>Required</code></strong></em>   <br>Your credentials with Twitter as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Twitter</code></td></tr><tr><td><code>Pixel Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Your pixel identifier as created in <a href="https://ads.twitter.com">Ads Manager</a> (E.g. "o8z6j", without quotes). More details are available by following this <a href="https://developer.twitter.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api">LINK</a> (See section "Steps" → "Creating the Conversion API event").</td></tr><tr><td><code>Event Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Your event identifier as created in <a href="https://ads.twitter.com">Ads Manager</a> (E.g. "tw-o8z6j-o8z21", without quotes). More details are available by following this <a href="https://developer.twitter.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api">LINK</a> (See section "Steps" → "Creating the Conversion API event").</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | X Conversion Events    |
| ---------------------- | ---------------------- |
| `[Any Event]` **\[1]** | `[Any Event]` **\[2]** |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.\
**\[2]** See <mark style="color:blue;">`Event Id`</mark> in [Configuration](x-twitter-conversion-api.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All X properties are set in the object <mark style="color:blue;">`conversions[0]`</mark> . More details are available by following this [LINK](https://developer.twitter.com/en/docs/twitter-ads-api/measurement/api-reference/conversions).
{% endhint %}

{% hint style="warning" %}
At least one of the following must be included:\
•  Twitter click identifier (twclid)\
•  Hashed email\
•  Hashed [E164](https://en.wikipedia.org/wiki/E.164) phone number

Having more values increases the match rate. More details are available by following this [LINK](https://developer.x.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api) (See section "Preparing Identifiers for Conversion Events").
{% endhint %}

<table><thead><tr><th width="348.6685580062746">Commanders Act Properties</th><th>X Properties</th></tr></thead><tbody><tr><td><code>context.event_timestamp</code></td><td><code>conversion_time</code> <strong>[*]</strong></td></tr><tr><td><code>Event Id</code></td><td><code>event_id</code> <strong>[*]</strong></td></tr><tr><td><code>partners.twitter.twclid</code></td><td><code>identifiers.X.twclid</code> <strong>[1]</strong></td></tr><tr><td><code>user.email</code></td><td><code>identifiers.X.hashed_email</code> <strong>[1]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>identifiers.X.hashed_phone_number</code> <strong>[1]</strong></td></tr><tr><td><code>items.length</code></td><td><code>number_items</code></td></tr><tr><td><code>currency</code></td><td><code>price_currency</code></td></tr><tr><td><code>value</code></td><td><code>value</code></td></tr><tr><td><code>id</code></td><td><code>conversion_id</code> <strong>[2]</strong></td></tr><tr><td><code>type</code></td><td><code>description</code></td></tr><tr><td><code>search_term</code></td><td><code>search_string</code></td></tr><tr><td><code>items.X.id</code></td><td><code>contents.X.content_id</code></td></tr><tr><td><code>items.X.product.group_id</code></td><td><code>contents.X.content_group_id</code></td></tr><tr><td><code>items.X.product.name</code></td><td><code>contents.X.content_name</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>contents.X.content_price</code></td></tr><tr><td><code>items.X.product.category_1</code>  <code>items.X.product.category_2</code>  <code>items.X.product.category_3</code> <code>items.X.product.category_4</code> <code>items.X.product.category_5</code></td><td><code>contents.X.content_type</code> <strong>[3]</strong></td></tr><tr><td><code>items.X.quantity</code></td><td><code>contents.X.num_items</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** At least one of these properties must be provided.\
**\[2]** For deduplication purpose, ensure you use the same value with your [Twitter Pixel](https://business.twitter.com/en/help/campaign-measurement-and-analytics/conversion-tracking-for-websites.html). More details are available by following this [LINK](https://developer.twitter.com/en/docs/twitter-ads-api/measurement/web-conversions/conversion-api) (See section "Duplication between Pixel and Conversion API").\
**\[3]** Categories are separated by the greater than (>) character.&#x20;
{% endhint %}
