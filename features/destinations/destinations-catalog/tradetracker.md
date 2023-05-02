# TradeTracker

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[TradeTracker](https://tradetracker.com) is an affiliate marketing network and a team of result driven affiliate professionals, devoted to performance marketing and always looking to get best results.\
Using this destination you can implement [server-side tracking](https://sc.tradetracker.net/implementation/overview?f\[id]=31).

## Key features

The TradeTracker destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [TradeTracker lead and sale tracking](https://sc.tradetracker.net/implementation/overview?f\[id]=31), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

{% hint style="info" %}
Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to refine events and/or other properties matching your specific needs.
{% endhint %}

### Configuration

| Settings                | Description                                                                                                                                                                                                                                                       |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Conversion Type`       | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>Sale</code> or <code>Lead</code>. </p>                                                                                    |
| `Campaign Id`           | <p><em><strong><code>Required</code></strong></em><br>Your campaign identifier as provided by TradeTracker. More details are available following this <a href="https://sc.tradetracker.net/implementation/overview?f[id]=31">LINK</a>. <strong>[1]</strong></p>   |
| `Product Id`            | <p><em><strong><code>Required</code></strong></em><br>Your product identifier as provided by TradeTracker. More details are available following this <a href="https://sc.tradetracker.net/implementation/overview?f[id]=31">LINK</a>. <strong>[1]</strong></p>    |
| `Click Id`              | <p><em><strong><code>Required</code></strong></em><br>Your event property holding the TradeTracker click identifier. More details are available following this <a href="https://sc.tradetracker.net/implementation/overview?f[id]=31">LINK</a>.</p>               |
| `Merchant Description`  | Your event property holding merchant description data and used for statistical purpose. Visible for merchant only. More details are available following this [LINK](https://sc.tradetracker.net/implementation/overview?f\[id]=31).                               |
| `Affiliate Description` | Your event property holding affiliate description data and used by affiliates affiliates for campaign optimisation. Visible for affiliates only. More details are available following this [LINK](https://sc.tradetracker.net/implementation/overview?f\[id]=31). |

{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).
{% endhint %}

## Quick reference

| Commanders Act Events   | TradeTracker Tracking |
| ----------------------- | --------------------- |
| `[Any events]` **\[1]** | `lead`                |
| `[Any events]` **\[1]** | `sale`                |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify the matching event.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

| Commanders Act Properties | TradeTracker Properties   |
| ------------------------- | ------------------------- |
| `Campaign Id`             | `cid` **\[\*]**           |
| `Product Id`              | `pid` **\[\*]**           |
| `Click Id`                | `data` **\[\*]**          |
| `id`                      | `tid` **\[\*]**           |
| `value`                   | `tam` **\[1]**            |
| `currency`                | `currency`                |
| `items.length`            | `qty`                     |
| `coupon`                  | `vc`                      |
| `Merchant Description`    | `descrMerchant` **\[2]**  |
| `Affiliate Description`   | `descrAffiliate` **\[3]** |

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** Mandatory for "Sale" conversion type.\
**\[2]** Merchant description data used for statistical purpose. Visible for merchant only.\
**\[3]** Affiliate description data used by affiliates for campaign optimisation. Visible for affiliates only.
{% endhint %}
