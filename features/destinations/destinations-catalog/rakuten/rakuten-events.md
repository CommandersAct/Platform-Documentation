# Rakuten Events

[Rakuten Advertising](https://rakutenadvertising.com/) is an affiliate platform that provide data-driven products and platforms to fuel advertiser and publisher connections at scale, creating relevant matches that activate audiences and accelerate performance. Using this destination you can implement server-side tracking.

{% hint style="info" %}
This destination is currently under final review and it will be released soon.\
Contents are subjected to changes.
{% endhint %}

## Key features

The Rakuten Advertising destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Rakuten Advertising lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Rakuten Advertising.

## Destination setup

{% hint style="info" %}
Rakuten Advertising adds a URL parameter<mark style="color:blue;">`ranSiteID`</mark>to your landing page by default. This mandatory values is usually stored in a cookie called **rmStore**, **** which needs to be included in your events. Alternatively, you have the option to send its values by providing it in the following field:<mark style="color:blue;">`Rakuten Affiliate Tracking Id (tr)`</mark>**\[1]**. \
The cookie **rmStore** is also used to retrieve the mandatory property<mark style="color:blue;">`land`</mark>, which can also be sent using the field<mark style="color:blue;">`Rakuten User Arrival (land)`</mark>**\[1]**. \
See [Field Mappings](rakuten-events.md#field-mappings) for more details.\
\
**\[1]** "Smart Mapping" field.
{% endhint %}

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Affiliate Merchant Id`   | <p><em><strong><code>Required if</code></strong></em><strong><code>Rakuten Affiliate Merchant Id (mid) is not set</code></strong></p><p>Your unique "Affiliate Merchant Id" as provided by Rakuten.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `Mapping`                 | <p><em><strong><code>Required</code></strong></em><br>Map "Rakuten Conversion Type" with your Commanders Act event(s) by setting at least a <code>Rakuten Conversion Type</code> and a <code>Commanders Act Event Name</code>. One entry is required.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `Custom Event Properties` | <p>Map your custom event properties by setting their field names in <code>Event property name</code> and adding the field name holding the value <strong></strong> in <code>Commanders Act event property</code>. E.g. if you input<code>size</code>in the <code>Event property name</code> and <code>properties.items.0.product.size</code> in <code>Commanders Act event property or static value</code>, you'll have a custom event property in Rakuten Advertising called<code>size</code>with a value based on the content of the field <code>properties.items.0.product.size</code> <strong>[1]</strong>.<br><br>In the column <code>Commanders Act event property position</code> you should keep the default value <code>Default</code> as it better fits most  scenarios. In case you select either <code>In "items" {items.X}</code> or <code>In "product" {items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and concatenate values separated by a pipe character ("|"). In this scenario, the property name used will be the one set in the <code>Event property name</code> plus the string "list" appended in the end.</p> |
| `Gateway Cookie Name`     | Your publisher links in Rakuten Advertising will direct users to a gateway page that sets a cookie holding key values. If you're not using the default cookie name ("rmStore"), enter its new name here.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Rakuten Conversion Type |
| --------------------- | ----------------------- |
| `[All events]`        | `Sale` or `Lead`        |

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Rakuten Advertising has two different endpoints: default "ep" commissionable and "eventnvppixel" media optimization pixel. Using the "Smart Mapping" field<mark style="color:blue;">`Rakuten Tracking Endpoint`</mark>you can select which one you want to use: set "mop" for the "eventnvppixel" media optimization or "ep" for the standard endpoint. Please note that there are limitations in terms of parameters you can send when selecting the "eventnvppixel" media optimization pixel.\
For the<mark style="color:blue;">`Lead`</mark>conversion type, if you don't provide item information such as identifier, quantity and name, the following fixed values are set<mark style="color:blue;">`skulist=Lead`</mark>, <mark style="color:blue;">`qlist=1`</mark>and <mark style="color:blue;">`namelist=Lead`</mark>. Moreover, if<mark style="color:blue;">`amtlist`</mark>can't be valorized with the provided information, it will be statically set as follow:<mark style="color:blue;">`amtlist=1`</mark>.\
More details on Rakuten properties are available following this [LINK](https://rak.app.box.com/s/j3qtvbd300vqa1zyknxklx3itqyi0vlh).
{% endhint %}

| Commanders Act Properties                                                                                                                                | Rakuten Properties             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| <p><code>Rakuten Affiliate Merchant Id (mid)</code> <strong>[1]</strong> or</p><p><code>Affiliate Merchant Id</code> </p>                                | `mid` **\[\*]\[2]**            |
| <p><code>partners.rakuten.land</code> or<br><code>Gateway Cookie Name</code></p>                                                                         | `land` **\[\*]\[3]**           |
| <p><code>partners.rakuten.tr</code> or<br><code>Gateway Cookie Name</code></p>                                                                           | `tr` **\[\*]\[4]**             |
| `id`                                                                                                                                                     | `ord`                          |
| `currency`                                                                                                                                               | `cur` **\[\*]**                |
| (`items.X.product.price` \* `items.X.quantity` \* 100) or (`revenue` \* 100)                                                                             | `amtlist` **\[\*]\[5]\[6]**    |
| `items.X.id`                                                                                                                                             | `skulist` **\[\*]\[6]**        |
| `items.X.quantity`                                                                                                                                       | `qlist` **\[\*]\[6]**          |
| `items.X.product.brand`                                                                                                                                  | `brandlist` **\[6]**           |
| `items.X.product.category_1` > `items.X.product.category_2` > `items.X.product.category_3` > `items.X.product.category_4` > `items.X.product.category_5` | `catlist` **\[6]**             |
| `items.X.coupon`                                                                                                                                         | `couponlist` **\[6]**          |
| `items.X.product.name`                                                                                                                                   | `namelist` **\[6]**            |
| `id_variant`                                                                                                                                             | `altord`                       |
| `context.device.advertising_id`                                                                                                                          | `did`                          |
| `discount`                                                                                                                                               | `discount`                     |
| `discount`                                                                                                                                               | `disamt`                       |
| `user.id`                                                                                                                                                | `custid`                       |
| `user.status`                                                                                                                                            | `custstatus`                   |
| `coupon`                                                                                                                                                 | `coupon`                       |
| `status`                                                                                                                                                 | `ordstatus`                    |
| `Commanders Act event property`                                                                                                                          | `Event property name` **\[7]** |

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** "Smart Mapping" field.\
**\[2]**<mark style="color:blue;">`Rakuten Affiliate Merchant Id (mid)`</mark>has priority over<mark style="color:blue;">`Affiliate Merchant Id`</mark>.\
**\[3]**<mark style="color:blue;">`partners.rakuten.land`</mark>has priority over<mark style="color:blue;">`Gateway Cookie Name`</mark>.\
<mark style="color:blue;">`partners.rakuten.land`</mark>must be in the 24-hour format: <mark style="color:blue;">`yyyymmdd_hhmm`</mark>.\
**\[4]**<mark style="color:blue;">`partners.rakuten.tr`</mark>has priority over<mark style="color:blue;">`Gateway Cookie Name`</mark>.\
**\[5]** if items are reported in your item list, this is computed using the item price and item quantity, otherwise, the revenue is used. Multiplying by 100 is not applied when<mark style="color:blue;">`currency`</mark>is set with<mark style="color:blue;">`JPN`</mark>.\
**\[6]** Distinct product information is separated with a pipe character ("|").\
**\[7]** See<mark style="color:blue;">`Custom Event Properties`</mark>in [Configuration](rakuten-events.md#configuration) for more details.\

{% endhint %}
