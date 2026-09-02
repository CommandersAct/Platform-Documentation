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

# Effinity

[Effinity](https://www.effinity.fr/) is a digital acquisition agency.\
Using Effinity server-side tracking you can track lead and sale conversions.

## Key features

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) suits Effinity lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.

## Destination setup

{% hint style="info" %}
Ensure you can provide mandatory "Id Compteur" using one of the following:

* `Id Compteur` input field.
* `partners.effinity.id_compteur` property field.
* `Effinity Cookie Name`

See more details in the [Configuration](effinity.md#configuration) and [Field mappings](effinity.md#field-mappings) sections.
{% endhint %}

### Configuration

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your unique advertiser identifier as provided by Effinity.</td></tr><tr><td><code>Id Compteur</code></td><td><em><code>Required</code></em> <em><strong>if not provided through alternative methods: see</strong></em> <a href="effinity.md#destination-setup"><em><strong>Destination setup</strong></em></a><em><strong>.</strong></em><br>The only information necessary for attribution as it's used to identify the ad.</td></tr><tr><td><code>Prod Id</code></td><td>Optional information to identify the product at the origin of the transaction. This can also be provided through the <code>Effinity Cookie Name</code> field.</td></tr><tr><td><code>Effi Id</code></td><td>Optional information used by partners. This can also be provided through the <code>Effinity Cookie Name</code> field.</td></tr><tr><td><code>Effi Id2</code></td><td>Optional information used by partners. This can also be provided through the <code>Effinity Cookie Name</code> field.</td></tr><tr><td><code>Conversion Type</code></td><td><em><strong><code>Required</code></strong></em><br>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code> . If conversion type is <code>lead</code> , only <code>generate_lead</code> events are forwarded to Awn. If conversion type is <code>sale</code> , only <code>purchase</code> events are sent to the partner.</td></tr><tr><td><code>Effinity Cookie Name</code></td><td>Enter a cookie name holding Effinity key landing values. Expected cookie structure: "[ID_COMPTEUR],[PROD_ID],[EFFI_ID],[EFFI_ID2]" (E.g. "01010101,1234,567890,098765", without quotes). <strong>[1]</strong></td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Effinity property name</code> and adding the value in <code>Your value</code>. <code>Effinity property name</code> must be set with <code>refX</code> where <code>X</code> is a number from 2 to 20 (inclusive).</td></tr></tbody></table>

{% hint style="info" %}
**1.** See [Destination setup](effinity.md#destination-setup) and [Field Mappings](effinity.md#field-mappings) for more details.
{% endhint %}

## Quick reference

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Commanders Act Events</th><th>Effinity Tracking</th></tr></thead><tbody><tr><td><code>generate_lead</code></td><td><code>lead</code></td></tr><tr><td><code>purchase</code></td><td><code>sale</code></td></tr></tbody></table>

## Field mappings

{% hint style="info" %}
The Effinity property <mark style="color:blue;">`consent_performance`</mark> is always set to <mark style="color:blue;">`1`</mark> . Manage your consent settings using the filter tab of this destination (See [Destination filters](https://doc.commandersact.com/features/destinations/destination-filters)).
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Fields</th><th>Commanders Act Properties</th><th>Effinity Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>Advertiser Id</code></td><td><code>id</code></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>monnaie</code></td></tr><tr><td><code>Transaction Revenue</code></td><td><code>revenue</code></td><td><code>montant</code></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>ref</code></td></tr><tr><td><code>-</code><br><code>-</code><br><code>-</code></td><td><p><code>Id Compteur</code></p><p><code>partners.effinity.id_compteur</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>id_compteur</code> <strong>[1]</strong></td></tr><tr><td><code>-</code><br><code>-</code><br><code>-</code></td><td><p><code>Prod Id</code></p><p><code>partners.effinity.prod_id</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>prod_id</code> <strong>[1]</strong></td></tr><tr><td><code>-</code><br><code>-</code><br><code>-</code></td><td><p><code>Effi Id</code><br><code>partners.effinity.effi_id</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>effi_id</code> <strong>[1]</strong></td></tr><tr><td><code>-</code><br><code>-</code><br><code>-</code></td><td><p><code>Effi Id2</code></p><p><code>partners.effinity.effi_id2</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>effi_id2</code> <strong>[1]</strong></td></tr><tr><td><code>Payment Method</code></td><td><code>payment_method</code></td><td><code>payment</code></td></tr><tr><td><code>Transaction Coupon</code></td><td><code>coupon</code></td><td><code>voucher</code></td></tr></tbody></table>

{% hint style="info" %}
**1.** Priority order listed on the column <mark style="color:blue;">`Commanders Act Properties`</mark> .
{% endhint %}
