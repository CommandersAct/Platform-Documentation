---
description: >-
  In this section, you will find all the events references supported by
  Commanders Act.
---

# Events reference

## Introduction

For each event, there is some properties required.&#x20;

In any cases, the following properties are required :&#x20;

* `event_name`
* `context.event_id`
* `context.event_timestamp`

Note : The commanders act [one tag](../../../getting-started/integrating-your-data/onetag-tutorial.md) and the [mobile sdks](../about-events/mobile-sdk-event-specificity.md) put automatically the context properties.

In this section you can find the list of all our standard events, with the list of standard properties required or not.

{% content-ref url="common-events.md" %}
[common-events.md](common-events.md)
{% endcontent-ref %}

{% content-ref url="e-commerce-events.md" %}
[e-commerce-events.md](e-commerce-events.md)
{% endcontent-ref %}

{% content-ref url="video-event-reference.md" %}
[video-event-reference.md](video-event-reference.md)
{% endcontent-ref %}

{% content-ref url="campaign-analytics-module-events.md" %}
[campaign-analytics-module-events.md](campaign-analytics-module-events.md)
{% endcontent-ref %}

If the event type or the properties you're looking for aren't mentioned in this section, you still can send custom events and custom properties. But the property `event_name` remains required.\
\
Here are the most used events:

## add\_payment\_info <a href="#add_payment_info" id="add_payment_info"></a>

This event signifies a user has submitted their payment information

**Parameters (required and recommended)**

<table><thead><tr><th width="137">Name</th><th width="101">Type</th><th width="76">Required</th><th width="147">Example Value</th><th width="288">Description</th></tr></thead><tbody><tr><td><code>payment_method</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>card</td><td>The chosen method of payment (see list of possible values below)</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list and is mandatory to manage consents. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>revenue</code></td><td><code>number</code></td><td>No</td><td>16.00</td><td><p>Revenue (shipping price and taxes <strong>excluded</strong>) after discount.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td>No</td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','add_payment_info', {
  payment_method: 'card',
  revenue: 16.00,
  currency: 'EUR',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCAddPaymentInfoEvent("card")
event.revenue = 16.00f
event.currency = "EUR"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCAddPaymentInfoEvent event = new TCAddPaymentInfoEvent("card");
event.revenue = 16.6f;
event.currency = "EUR";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCAddPaymentInfoEvent *event = [[TCAddPaymentInfoEvent alloc] initWithId: @"ID";
event.revenue = [[NSDecimalNumber alloc] initWithFloat: 16.00f];
event.currency = @"EUR";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCAddPaymentInfoEvent(payementMethod: "card")
	event?.revenue = 16.00
	event?.currency = "EUR"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCAddPaymentInfoEvent();
    event.paymentMethod = "card";
    event.revenue = 16.00;
    event.currency = "EUR";
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "add_payment_info",
        "payment_method": "card",
        "revenue": 16.00,
        "value": 22.53,
        "currency": "EUR",
        "user": {
            "id": "12345",
            "email": "toto@domain.fr",
            "consent_categories": [
                1,
                3
            ]
        }
}
```
{% endtab %}
{% endtabs %}

## add\_shipping\_info

This event signifies a user has submitted their shipping information.

#### Parameters <a href="#parameters_2" id="parameters_2"></a>

<table><thead><tr><th width="138">Name</th><th width="99">Type</th><th width="74">Required</th><th width="159">Example value</th><th width="281">Description</th></tr></thead><tbody><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>Yes</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> or <code>value</code>parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>value</code></td><td><code>number</code></td><td>Yes</td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>shipping_tier</code></td><td><code>string</code></td><td>No</td><td>Ground</td><td>The shipping tier (e.g. <code>Next-day</code>, Air`) selected for delivery of the purchased item.</td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','add_shipping_info', {
  value: 8.00,
  currency: 'EUR',
  coupon: 'promo',
  shipping_tier: 'ups',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCAddShippingInfoEvent(items,  112.5f, "EUR")
    event.coupon = "promo"
    event.shippingTier = "ups"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCAddShippingInfoEvent event = new TCAddShippingInfoEvent(items, 112.5f, "EUR");
event.coupon = "promo";
event.shippingTier = "ups";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1"
                                  withPrice: [[NSDecimalNumber alloc] initWithString: @"1.5"]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2" 
                                  withName: @"pName2" 
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCAddShippingInfoEvent *event = [[TCAddShippingInfoEvent alloc] initWithItems: items
withValue: [[NSDecimalNumber alloc] initWithString: @"12.2"]
withCurrency: @"EUR"];

event.coupon = @"promo";
event.shippingTier = @"ups";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCAddShippingInfoEvent(items: [item_1, item_2], withValue: 1, withCurrency: "EUR")
	event?.addAdditionalProperty("additionalKey", withBoolValue: true)
	event?.coupon = "promo"
	event?.shippingTier = "ups"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 150;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
TCProduct tc_product_2 = TCProduct();
		tc_product_2.ID = "product_2_ID";
		tc_product_2.name = "product_2_name";
		tc_product_2.price = 150;
		tc_product_2.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_2 = TCItem();
		tc_item_2.ID = "item_2_id";
		tc_item_2.quantity = 2;
		tc_item_2.product = tc_product;
		tc_item_2.addAdditionalProperty("key_additional_item", "val_additional_product");

var event = TCAddShippingInfoEvent();
    event.coupon = "promo";
    event.shippingTier = "ups";
    event.currency = "EUR";
    event.items = [tc_item_1, tc_item_2];
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "add_shipping_info",
        "shipping_tier": "Ground",
        "revenue": 16.00,
        "value": 22.53,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ],
                    "price": 9.99
                }
            },
            {
                "id": "SKU_12346",
                "quantity": 1,
                "price": 9.99,
                "variant": "green",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12346",
                    "name": "Heart tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "girl",
                    "brand": "Jenyfion",
                    "colors": [
                        "blue",
                        "white"
                    ],
                    "price": 9.99
                }
            }
        ],
        "user": {
            "id": "12345",
            "email": "toto@domain.fr",
            "consent_categories": [
                1,
                3
            ]
        }
}
```
{% endtab %}
{% endtabs %}

## add\_to\_cart

This event signifies that an item was added to a cart for purchase.

**Parameters (required and recommended)**

<table><thead><tr><th width="136">Name</th><th width="103">Type</th><th width="102">Required</th><th width="135">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong>*</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong>*</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','add_to_cart', {
  value: 8.00,
  currency: 'EUR',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCAddToCartEvent(22.53f,  "EUR", items)
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCAddToCartEvent event = new TCAddToCartEvent(22.53f,  "EUR", items);
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 1.5f]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2"
                                  withName: @"pName2"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCAddToCartEvent *event = [[TCAddToCartEvent alloc] initWithValue: [[NSDecimalNumber alloc] initWithString: @"12.2"]
withCurrency: @"EUR"
withItems: items];
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCAddToCartEvent(value: 1, withCurrency: "EUR", withItems: [item_1, item_2])
	event?.addAdditionalProperty("additionalKey", withBoolValue: true)
	event?.currency = "EUR"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 12.5;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");

var event = TCAddToCartEvent();
    event.currency = "EUR";
    event.items = [tc_item_1];
    event.value = 12.5;
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "add_to_cart",
        "value": 8.00,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ]
                }
            }
        ]
}
```
{% endtab %}
{% endtabs %}

## add\_to\_wishlist

The event signifies that an item was added to a wishlist. Use this event to identify popular gift items in your app.

**Parameters (required and recommended)**

<table><thead><tr><th width="142">Name</th><th width="100">Type</th><th width="80">Required</th><th width="157">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','add_to_wishlist', {
  value: 8.00,
  currency: 'EUR',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCAddToWishlistEvent(items)
    event.value = 20.00f
    event.currency = "EUR"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCAddToWishlistEvent event = new TCAddToWishlistEvent(items);
event.value = 20.00f;
event.currency = "EUR";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
    withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
    withName: @"pName1"
    withPrice: [[NSDecimalNumber alloc] initWithFloat: 1.5f]]
    withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
    withProduct: [[TCProduct alloc] initWithProductId: @"pID2"
    withName: @"pName2"
    withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
    withQuantity: 2]];

TCAddToWishlistEvent *event = [[TCAddToWishlistEvent alloc] initWithValue: [[NSDecimalNumber alloc] initWithString: @"12.2"]
withCurrency: @"EUR"
withItems: items];
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCAddToWishlistEvent(items: [item_1, item_2])
	event?.currency = "EUR"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 150;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");

var event = TCAddToWishlistEvent();
    event.addAdditionalPropertyWithIntValue("key_additional_1", 12);
    event.addAdditionalPropertyWithListValue("key_additional_2", [12,12,12]);
    event.currency = "EUR";
    event.items = [tc_item_1];
    event.value = 12.5;
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "add_to_wishlist",
        "value": 8.00,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ]
                }
            }
        ]
}
```
{% endtab %}
{% endtabs %}

## begin\_checkout <a href="#begin_checkout" id="begin_checkout"></a>

This event signifies that a user has begun a checkout.

**Parameters (required and recommended)**

<table><thead><tr><th width="138">Name</th><th width="98">Type</th><th width="78">Required</th><th width="157">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>16.00</td><td>The monetary value of the event (shipping price and taxes <strong>excluded</strong>) after discount</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong></td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>id</code></td><td><code>string</code></td><td>No</td><td>0_12345</td><td>Transaction id. Used as key for updates</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','begin_checkout', {
  id: 'O_12345',
  coupon: 'CHRISTMAS',
  revenue: 16.00,
  value: 20.33,
  currency: 'EUR',
  user: {
    id: '12356',
    email:'toto@domain.fr'
  },
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    price: 9.99,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      colors: ['red'],
      price: 9.99
    }
  }, {
    id: 'SKU_12346',
    quantity: 1,
    price: 9.99,
    variant: 'green',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12346',
      name: 'Heart tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'girl',
      brand: 'Jenyfion',
      colors: ['blue','white'],
      price: 9.99
    }
  }]
})
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCBeginCheckoutEvent(1.0f,  2.0f, "EUR", items)
    event.coupon = "CHRISTMAS"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCBeginCheckoutEvent event = new TCBeginCheckoutEvent(1.0f,  2.0f, "EUR", items);
event.coupon = "CHRISTMAS";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1" 
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 1.5f]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2" 
                                  withName: @"pName2" 
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCBeginCheckoutEvent *event = [[TCBeginCheckoutEvent alloc] initWithRevenue: [[NSDecimalNumber alloc] initWithString: @"1.1"]
withValue: [[NSDecimalNumber alloc] initWithString: @"12.2"]
withCurrency: @"EUR"
withItems: items];
event.coupon = @"CHRISTMAS";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCBeginCheckoutEvent(revenue: 1, withValue: 3, withCurrency: "EUR", withItems: [item_1, item_2])
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 10;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
TCProduct tc_product_2 = TCProduct();
		tc_product_2.ID = "product_2_ID";
		tc_product_2.name = "product_2_name";
		tc_product_2.price = 5.10;
		tc_product_2.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_2 = TCItem();
		tc_item_2.ID = "item_2_id";
		tc_item_2.quantity = 2;
		tc_item_2.product = tc_product;
		tc_item_2.addAdditionalProperty("key_additional_item", "val_additional_product");
var event = TCBeginCheckoutEvent();
    		event.coupon = "CHRISTMAS";
		event.items = [tc_item_1, tc_item_2];
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "begin_checkout",
        "id": "O_12345",
        "coupon": "CHRISTMAS",
        "revenue": 16.00,
        "value": 22.53,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ],
                    "price": 9.99
                }
            },
            {
                "id": "SKU_12346",
                "quantity": 1,
                "price": 9.99,
                "variant": "green",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12346",
                    "name": "Heart tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "girl",
                    "brand": "Jenyfion",
                    "colors": [
                        "blue",
                        "white"
                    ],
                    "price": 9.99
                }
            }
        ],
        "user": {
            "id": "12345",
            "email": "toto@domain.fr",
            "consent_categories": [
                1,
                3
            ]
        }
}
```
{% endtab %}
{% endtabs %}

## generate\_lead <a href="#generate_lead" id="generate_lead"></a>

Log this event when a lead has been generated to understand the efficacy of your re-engagement campaigns.

**Parameters (required and recommended)**

<table><thead><tr><th width="134">Name</th><th width="103">Type</th><th width="77">Required</th><th width="144">Example Value</th><th width="288">Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td><strong>No</strong>*</td><td>9.99</td><td><p>The monetary value of the event.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>No*</strong></td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>id</code></td><td><code>string</code></td><td>No</td><td></td><td>Lead id</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','generate_lead', {
  currency: 'EUR',
  value: 9.99,
  id: 'L_12345',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCGenerateLeadEvent(9.99f, "EUR")
event.ID = "L_12345"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCGenerateLeadEvent event = new TCGenerateLeadEvent(9.99f, "EUR");
event.ID = "L_12345";
serverside.execute(event);TCLoginEvent event = new TCLoginEvent();
event.method = "LinkedIn";
serverside.execute(event);

```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCGenerateLeadEvent *event = [[TCGenerateLeadEvent alloc] initWithValue: [[NSDecimalNumber alloc] initWithString: @"12.2"]
withCurrency: @"EUR"];
event.ID = @"2b758628-f81b-454f-8e3d-867e8bc98523";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCGenerateLeadEvent(value: 1, withCurrency: "EUR")
    event?.ID = "2b758628-f81b-454f-8e3d-867e8bc98523";
    serverside.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCGenerateLeadEvent();
    event.currency = "EUR";
    event.value = 9.99;
    event.ID = "2b758628-f81b-454f-8e3d-867e8bc98523";
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "generate_lead",
        "method": "LinkedIn"
}
```
{% endtab %}
{% endtabs %}

## login <a href="#login" id="login"></a>

Send this event to signify that a user has logged in.

#### Parameters <a href="#parameters_14" id="parameters_14"></a>

<table><thead><tr><th width="119">Name</th><th width="103">Type</th><th width="77">Required</th><th width="224">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>method</code></td><td><code>string</code></td><td>No</td><td>LinkedIn</td><td>The method used to login.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger', 'login', {
  method: 'LinkedIn',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCLoginEvent()
event.method = "LinkedIn"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCLoginEvent event = new TCLoginEvent();
event.method = "LinkedIn";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCLoginEvent *event = [[TCLoginEvent alloc] init];
event.method = @"LinkedIn";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCLoginEvent()
	event.method = "linkedin"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCLoginEvent();
    event.method = "LinkedIn";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "login",
        "method": "LinkedIn"
}
```
{% endtab %}
{% endtabs %}

## page\_view <a href="#page_view" id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

**Parameters (required and recommended)**

<table><thead><tr><th width="144">Name</th><th width="99">Type</th><th width="82">Required</th><th width="160">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>page_type</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>product_list</td><td><p>Page category. Recommended predefined types:</p><ul><li>home</li><li>landing</li><li>product_list</li><li>product</li><li>content_list</li><li>content</li><li>search</li><li>funnel</li><li>success</li><li>funnel_confirmation</li><li>account</li><li>cart</li><li>legal (e.g. Privacy Policy)</li></ul><p>Equivalent to <code>tc_vars.env_template</code></p></td></tr><tr><td><code>page_name</code></td><td><code>string</code></td><td>No</td><td>Suggestion for Mother's Day</td><td>Name of the page.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>type</code><br>(deprecated)</td><td><code>string</code></td><td>No</td><td>product_list</td><td>Page category</td></tr></tbody></table>

**Automatically added parameters by cact API for web sources**

<table><thead><tr><th width="133">Name</th><th width="103">Type</th><th width="81">Required</th><th width="161">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>user</code></td><td><a href="./#user">Object &#x3C;User></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>title</code></td><td><code>string</code></td><td>No</td><td>Products - MySite.com</td><td>Title of the page :<a href="https://developer.mozilla.org/en-US/docs/Web/API/Document/title"><code>document.title</code></a> from the DOM API</td></tr><tr><td><code>url</code></td><td><code>string</code></td><td>No</td><td><a href="http://www.mysite.com">http://www.mysite.com</a></td><td>Full URL of the page. Equivalent to<a href="https://developer.mozilla.org/en-US/docs/Web/API/Location"><code>location.href</code></a> from the DOM API.</td></tr><tr><td><code>path</code></td><td><code>string</code></td><td>No</td><td>/products/mothers</td><td>Path portion of the URL of the page : <a href="https://developer.mozilla.org/en-US/docs/Web/API/Location"><code>location.pathname</code></a> from the DOM API.</td></tr><tr><td><code>referrer</code></td><td><code>string</code></td><td>No</td><td><a href="http://www.example.com">http://www.example.com</a></td><td>Full URL of the previous page : <a href="https://developer.mozilla.org/en-US/docs/Web/API/Document/referrer"><code>document.referrer</code></a> from the DOM API.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger','page_view', {
  page_type: 'product_list',
  page_name: 'Best sellers',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCPageViewEvent("product_list")
event.pageName = "Best sellers"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCPageViewEvent event = new TCPageViewEvent("product_list")
event.pageName = "Best sellers";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCPageViewEvent *event = [[TCPageViewEvent alloc] init];
event.pageType = @"product_list";
event.pageName = @"Best sellers";
[TCS execute: event];

//or you could also use it in a constructor, as follow:
TCPageViewEvent *event = [[TCPageViewEvent alloc] initWithType: @"type"];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCPageViewEvent(type: "product list")
	event?.pageName = "Best sellers"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCPageViewEvent();
    event.pageName = "event_page_name";
    event.pageType = "event_page_type";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "page_view", 
        "page_type": "product_list",
        "page_name": "Best sellers"   
}
```
{% endtab %}
{% endtabs %}

## purchase

Fire this event when one or more items are purchased by a user.

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="182">Name</th><th width="113">Type</th><th>Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>O_1245</td><td>Transaction id. Used as key for updates</td></tr><tr><td><code>event_name</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>purchase</td><td>Have to be purchase</td></tr><tr><td><code>type</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>offline</td><td>Type of conversion (online, offline, call etc.)</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>22.53</td><td>The final price of the conversion (shipping and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>16.00</td><td>The final price of the conversion (shipping and taxes <strong>excluded</strong>) after discount</td></tr><tr><td><code>payment_method</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>card</td><td>Payment method type (see list of <a href="./#payment-methods">possible values</a> below)</td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong></td><td>EUR</td><td>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</td></tr><tr><td><code>status</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>in_progress</td><td>Status of the conversion (see list of <a href="./#purchase-status">possible values</a> below).<br><em>Conversions with status "pending" are not included in default sum and counts aggregated on augmented user attributes feature</em></td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td><strong>Yes</strong></td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3],</code> </p><p><code>card:3320457845</code>  </p><p><code>}</code></p></td><td><p>All properties that you add here will be used as conditions for matching users in our database.</p><p><code>consent_categories</code> is automatically filled if you use Commanders Act CMP.</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>tax_amount</code></td><td><code>number</code></td><td>No</td><td>3.20</td><td>Amount of the taxes at the end of the conversion</td></tr><tr><td><code>shipping_amount</code></td><td><code>number</code></td><td>No</td><td>3.33</td><td>Shipping cost associated with a transaction.</td></tr><tr><td><code>shipping_provider</code></td><td><code>string</code></td><td>No</td><td>Post</td><td>Provider information</td></tr><tr><td><code>discount_value</code></td><td><code>number</code></td><td>No</td><td>3.98</td><td>Amount of discount (tax <strong>included</strong>)</td></tr><tr><td><code>original_value</code></td><td><code>number</code></td><td>No</td><td>19.98</td><td>First price for the original conversion (taxes <strong>included</strong>)</td></tr><tr><td><code>original_revenue</code></td><td><code>number</code></td><td>No</td><td>16.78</td><td>First revenue for the original conversion (taxes <strong>excluded</strong>)</td></tr><tr><td><code>original_tax_amount</code></td><td><code>number</code></td><td>No</td><td>3.20</td><td>Amount of the taxes at the beginning of the conversion</td></tr><tr><td><code>returned_value</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Amount of returned items (taxes <strong>included</strong>)</td></tr><tr><td><code>returned_quantity</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Quantity of returned items (taxes <strong>included</strong>)</td></tr><tr><td><code>cancelled_value</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Amount of cancelled items (taxes <strong>included</strong>)</td></tr><tr><td><code>cancelled_quantity</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Quantity of cancelled items (taxes <strong>included</strong>)</td></tr></tbody></table>

**Automatically added by cact API**

| Name  | Type        | Required | Example | Description                                                                                   |
| ----- | ----------- | -------- | ------- | --------------------------------------------------------------------------------------------- |
| `url` | string(url) | No       | none    | <p>URL to the website where you can buy the item</p><p>Equivalent to window.location.href</p> |

**Example**

{% tabs %}
{% tab title="json" %}
```json
{
   "id": "O_12345",
   "event_name": "purchase",
   "type": "offline",
   "value": 0,
   "revenue": 16.00,
   "payment_method": "card",
   "currency": "EUR",
   "status": "in_progress",
   "user": {
      "id": "12345",
      "email": "toto@domain.fr",
      "consent_categories": [
         1,
         3
      ],
      "card": "3320457845"
   },
   "context": {
      "event_id": "2025uaoauud",
      "event_timestamp": "2025-04-18T07:53:39.974+02:00"
   },
   "items": [
      {
         "id": "SKU_12345",
         "quantity": 1,
         "price": 9.99,
         "variant": "red",
         "discount": 1.99,
         "value": 8.0,
         "cancelled_value": 0,
         "cancelled_quantity": 0,
         "original_value": 9.99,
         "returned_value": 0,
         "returned_quantity": 0,
         "product": {
            "id": "12345",
            "name": "Trex tshirt",
            "category_1": "clothes",
            "category_2": "t-shirts",
            "category_3": "boy",
            "brand": "Lacoste",
            "colors": [
               "red"
            ],
            "price": 9.99
         }
      },
      {
         "id": "SKU_12346",
         "quantity": 1,
         "price": 9.99,
         "variant": "green",
         "coupon": "CHRISTMAS",
         "discount": 1.99,
         "value": 8.0,
         "cancelled_value": 0,
         "cancelled_quantity": 0,
         "original_value": 9.99,
         "returned_value": 0,
         "returned_quantity": 0,
         "product": {
            "id": "12346",
            "name": "Heart tshirt",
            "category_1": "clothes",
            "category_2": "t-shirts",
            "category_3": "girl",
            "brand": "Jenyfuen",
            "colors": [
               "blue",
               "white"
            ],
            "price": 9.99
         }
      }
   ],
   "coupon": "CHRISTMAS",
   "tax_amount": 3.20,
   "shipping_amount": 3.33,
   "shipping_provider": "Post",
   "discount_value": 3.98,
   "original_value": 19.98,
   "original_revenue": 16.78,
   "original_tax_amount": 3.20,
   "returned_value": 0,
   "returned_quantity": 0,
   "cancelled_value": 0,
   "cancelled_quantity": 0
}
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
cact('trigger','purchase', {
  id: 'O_12345',
  coupon: 'CHRISTMAS',
  revenue: 16.00,
  value: 20.33,
  shipping_amount: 3.33,
  tax_amount: 3.20,
  currency: 'EUR',
  user: {
    id: '12356',
    email:'toto@domain.fr'
  },
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    price: 9.99,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      colors: ['red'],
      price: 9.99
    }
  }, {
    id: 'SKU_12346',
    quantity: 1,
    price: 9.99,
    variant: 'green',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12346',
      name: 'Heart tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'girl',
      brand: 'Jenyfion',
      colors: ['blue','white'],
      price: 9.99
    }
  }]
})
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCPurchaseEvent("O_12345", 16.0f,  22.53f, "EUR", "purchase", "CreditCard", "waiting", items)
    event.shippingAmount = 3.33f
    event.taxAmount = 3.20f
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCPurchaseEvent event = new TCPurchaseEvent("O_12345", 16.0f,  22.53f, "EUR", "purchase", "CreditCard", "waiting", items);
event.shippingAmount = 3.33f;
event.taxAmount = 3.20f;
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1" 
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1"
                                  withName: @"pName1"
                                  withPrice: [[NSDecimalNumber alloc] initWithString: @"1.5"]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2"
                                  withName: @"pName2"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCPurchaseEvent *event = [[TCPurchaseEvent alloc] initWithId: @"ID"
withRevenue: [[NSDecimalNumber alloc] initWithString: @"1.1"]
withValue: [[NSDecimalNumber alloc] initWithString: @"12.2"]
withCurrency: @"EUR"
withType: @"purchase"
withPaymentMethod: @"CreditCard"
withStatus: @"waiting"
withItems: items];

[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCPurchaseEvent(id: "purchaseID", withRevenue: 16.21, withValue: 23.10, withCurrency: "EUR", withType: "purchase", withPaymentMethod: "CreditCard", withStatus: "waiting", withItems: [item_1, item_2])
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 10;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
TCProduct tc_product_2 = TCProduct();
		tc_product_2.ID = "product_2_ID";
		tc_product_2.name = "product_2_name";
		tc_product_2.price = 5.10;
		tc_product_2.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_2 = TCItem();
		tc_item_2.ID = "item_2_id";
		tc_item_2.quantity = 2;
		tc_item_2.product = tc_product;
		tc_item_2.addAdditionalProperty("key_additional_item", "val_additional_product");
var event = TCPurchaseEvent();
    		event.shippingAmount = 3.33;
    		event.taxAmount = 3.20;
    		event.revenue = 2.5;
		event.value = 12.2;
		event.currency = "EUR";
		event.type = "purchase";
		event.paymentMethod = "CreditCard";
		event.status = "waiting";
		event.items = [tc_item_1, tc_item_2];
serverside.execute(event);
```
{% endtab %}
{% endtabs %}

## refund

Fire this event when a purchase was refund

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="182">Name</th><th width="99">Type</th><th width="76">Required</th><th width="154">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>O_1245</td><td>Transaction id. Used as key for updates</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p>All properties that you add here will be used as conditions for matching users in our database.</p><p><code>consent_categories</code> is automatically filled if you use Commanders Act CMP.</p></td></tr><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>16.00</td><td>The monetary value of the event (shipping price and taxes <strong>excluded</strong>) after discount</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>shipping_amount</code></td><td><code>number</code></td><td>No</td><td>3.33</td><td>Shipping cost associated with a transaction.</td></tr><tr><td><code>tax_amount</code></td><td><code>number</code></td><td>No</td><td>3.20</td><td>Shipping cost associated with a transaction.</td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong></td><td>EUR</td><td>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>type</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>offline</td><td>Type of conversion (online, offline, call etc.)</td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td>No*</td><td></td><td>(*) <code>items</code> is required for partial refunds but it can be omitted for full refunds.</td></tr></tbody></table>

**Automatically added by cact API**

<table><thead><tr><th width="128">Name</th><th width="115">Type</th><th width="103">Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td><code>url</code></td><td>string(url)</td><td>No</td><td>none</td><td><p>URL to the website where you can buy the item</p><p>Equivalent to window.location.href</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','refund', {
  id: 'O_12345',
  coupon: 'CHRISTMAS',
  revenue: 16.00,
  value: 20.33,
  shipping_amount: 3.33,
  tax_amount: 3.20,
  currency: 'EUR',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
})
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCRefundEvent("O_12345", 16.00f, 23.53f, "EUR", "offline")
    event.coupon = "CHRISTMAS"
    event.shippingAmount = 4.33f
    event.taxAmount = 3.20f
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCRefundEvent event = new TCRefundEvent("O_12345", 16.00f, 23.53f, "EUR", "offline");
event.coupon = "CHRISTMAS";
event.shippingAmount = 4.33f;
event.taxAmount = 3.20f;
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1"
                                  withName: @"pName1"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 1.5f]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2"
                                  withName: @"pName2"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCRefundEvent *event = [[TCRefundEvent alloc] initWithID: @"2b758628-f81b-454f-8e3d-867e8bc98523"
withRevenue: [[NSDecimalNumber alloc] initWithString: @"20.2"]
withValue: [[NSDecimalNumber alloc] initWithString: @"26.2"]
withCurrency: @"EUR"
withType: @"offline"
withItems: items];

[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCRefundEvent(id: "purchaseID", withRevenue: 16.32, withValue: 23.1, withCurrency: "EUR", withType: "refund", withItems: [item_1, item_2])
	event?.shippingAmount = 11
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCRefundEvent();
    event.currency = "EUR";
    event.value = 26.20;
    event.revenue = 20.20;
    event.coupon = "CHRISTMAS";
    event.shippingAmount = 4.33;
    event.taxAmount = 3.20;
    event.type = "offline";    
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "refund",
        "value": 8.00,
        "currency": "EUR",
        "revenue": 16.00,
        "shipping_amount": 3.33,
        "tax_amount": 3.20
}
```
{% endtab %}
{% endtabs %}

## remove\_from\_cart

This event signifies that an item was removed from a cart.

**Parameters (required and recommended)**

<table><thead><tr><th width="146">Name</th><th width="103">Type</th><th width="106">Required</th><th>Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','remove_from_cart', {
  value: 8.00,
  currency: 'EUR',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)
val event = TCRemoveFromCartEvent(items)
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCRemoveFromCartEvent event = new TCRemoveFromCartEvent(items);
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 1.5f]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2"
                                  withName: @"pName2"
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCRemoveFromCartEvent *event = [[TCRemoveFromCartEvent alloc] initWithItems: items];
event.value = [[NSDecimalNumber alloc] initWithString: @"12.2"];
event.currency = @"EUR";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCRemoveFromCartEvent(items: [item_1, item_2])
	event?.value = 22.53
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 10;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
var event = TCRemoveFromCartEvent();
		event.value = 15.1;
		event.currency = "EUR";		
		event.items = [tc_item_1];
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "remove_from_cart",
        "value": 8.00,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ]
                }
            }
        ]
}
```
{% endtab %}
{% endtabs %}

## search

Use this event to contextualize search operations. This event can help you identify the most popular content in your app.

#### Parameters <a href="#parameters_21" id="parameters_21"></a>

<table><thead><tr><th width="169">Name</th><th width="102">Type</th><th width="82">Required</th><th width="155">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>search_term</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>t-shirts</td><td>The term that was searched for.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','search', {
  search_term: 't-shirts',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCSearchEvent("t-shirts")
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```
// Some code
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCSearchEvent *event = [[TCSearchEvent alloc] init];
event.searchTerm = @"t-shirts";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
<pre class="language-swift"><code class="lang-swift">let event = TCSearchEvent(searchTerm: "t-shirts")
<strong>    serverside.execute(event)
</strong></code></pre>
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCSearchEvent();
    event.searchTerm = "t-shirts";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "search",
        "search_term": "t-shirts"
}
```
{% endtab %}
{% endtabs %}

## select\_content

This event signifies that a user has selected some content of a certain type. This event can help you identify popular content and categories of content in your app or click on internal promotion.

#### Parameters <a href="#parameters_22" id="parameters_22"></a>

<table><thead><tr><th width="175">Name</th><th width="100">Type</th><th width="76">Required</th><th width="159">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>content_type</code></td><td><code>string</code></td><td>No</td><td>product</td><td>The type of selected content.</td></tr><tr><td><code>item_id</code></td><td><code>string</code></td><td>No</td><td>I_12345</td><td>An identifier for the item that was selected.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','select_content', {
  content_type: 'product',
  item_id: 'I_12345',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCSelectContentEvent
event.contentType = "product"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCSelectContentEvent event = new TCSelectContentEvent();
event.contentType = "product";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCSelectContentEvent *event = [[TCSelectContentEvent alloc] init];
event.contentType = @"product";
event.itemID = @"I_12345";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCSelectContentEvent()
	event.contentType = "product"
	event.itemID = "I_12345"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCSelectContentEvent();
    event.contentType = "product";
    event.itemId = "I_12345";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "select_content",
        "content_type": "product",
        "item_id": "I_12345"
}
```
{% endtab %}
{% endtabs %}

## select\_item

This event signifies an item was selected from a list.

#### Parameters <a href="#parameters_23" id="parameters_23"></a>

<table><thead><tr><th width="192">Name</th><th width="105">Type</th><th width="71">Required</th><th width="124">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>item_list_name</code></td><td><code>string</code></td><td>No</td><td>Related products</td><td>The name of the list in which the item was presented to the user.</td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event. The <code>items</code> array is expected to have a single element, representing the selected item.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','select_item', {
  item_list_name: 'Related products',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
<pre class="language-kotlin"><code class="lang-kotlin">val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf&#x3C;TCItem>(item1, item2)

val event = TCSelectItemEvent(items);
<strong>    event.itemListName = "Related products"
</strong>serverside.execute(event);
</code></pre>
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCSelectItemEvent event = new TCSelectItemEvent(items);
event.itemListName = "Related products";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1" 
                                  withPrice:[[NSDecimalNumber alloc] initWithFloat: 1.5f]]
                                  withQuantity: 1]];

TCSelectItemEvent *event = [[TCSelectItemEvent alloc] initWithItems: items];
event.itemListName = @"Related products";

[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCSelectItemEvent(items: [item_1, item_2])
	event.itemListName = "Related products";
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 150;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
var event = TCSelectItemEvent();
		event.itemListName = "Related products";
		event.items = [tc_item_1];
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "select_item",
        "item_list_name": "Related products",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ]
                }
            }
        ]
}
```
{% endtab %}
{% endtabs %}

## sign\_up <a href="#sign_up" id="sign_up"></a>

This event indicates that a user has signed up for an account.

#### Parameters **(required and recommended)** <a href="#parameters_27" id="parameters_27"></a>

<table><thead><tr><th width="117">Name</th><th width="102">Type</th><th width="104">Required</th><th width="160">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>method</code></td><td><code>string</code></td><td>No</td><td>Facebook</td><td>The method used for sign up.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','sign_up', {
  method: 'email',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCSignUpEvent()
event.method = "email"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCSignUpEvent event = new TCSignUpEvent();
event.method = "email";
serverside.execute(event);

```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCSignUpEvent *event = [[TCSignUpEvent alloc] init];
event.method = @"email";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCSignUpEvent()
	event.method = "email"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCSignUpEvent();
    event.method = "email";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "sign_up",
        "method": "email"
}
```
{% endtab %}
{% endtabs %}

## view\_cart

This event signifies that a user viewed their cart.

**Parameters (required and recommended)**

<table><thead><tr><th width="147">Name</th><th width="102">Type</th><th width="76">Required</th><th width="163">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','view_cart', {
  value: 8.00,
  currency: 'EUR',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCViewCartEvent(items)
    event.value = 15.1f
    event.currency = "EUR"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCViewCartEvent event = new TCViewCartEvent(items);
event.value = 15.1f;
event.currency = "EUR";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1" 
                                  withPrice: [[NSDecimalNumber alloc] initWithString: @"1.5"]]
                                  withQuantity: 1]];

TCViewCartEvent *event = [[TCViewCartEvent alloc] initWithItems: items];
event.value = [[NSDecimalNumber alloc] initWithString: @"12.2"];
event.currency = @"EUR";

[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCViewCartEvent(items: [item_1, item_2])
	event?.value = 22.53
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 10;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
TCProduct tc_product_2 = TCProduct();
		tc_product_2.ID = "product_2_ID";
		tc_product_2.name = "product_2_name";
		tc_product_2.price = 5.10;
		tc_product_2.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_2 = TCItem();
		tc_item_2.ID = "item_2_id";
		tc_item_2.quantity = 2;
		tc_item_2.product = tc_product;
		tc_item_2.addAdditionalProperty("key_additional_item", "val_additional_product");

var event = TCViewCartEvent();
	event.value = 15.1;
	event.currency = "EUR";
	event.items = [tc_item_1, tc_item_2	
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "view_cart",
        "value": 8.00,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ]
                }
            }
        ]
}
```
{% endtab %}
{% endtabs %}

## view\_item

This event signifies that some content was shown to the user. Use this event to manage the most popular items viewed.

**Parameters (required and recommended)**

<table><thead><tr><th width="139">Name</th><th width="101">Type</th><th width="82">Required</th><th width="157">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong>*</td><td>9.99</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes*</strong></td><td>EUR</td><td>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="JavaScript" %}
```javascript
cact('trigger','view_item', {
  value: 9.99,
  currency: 'EUR',
  items: [{
    id: 'SKU_12345',
    quantity: 1,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCViewItem(items)
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCViewItem event = new TCViewItem(items);
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1" 
                                  withPrice: [[NSDecimalNumber alloc] initWithString: @"1.5"]]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2" 
                                  withName: @"pName2" 
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCViewItem *event = [[TCViewItem alloc] initWithItems: items];
event.revenue = [[NSDecimalNumber alloc] initWithString: @"12.2"];
event.currency = @"EUR";

[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCViewItem(items: [item_1, item_2])
	event?.revenue = 12.2
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 150;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
var event = TCViewItemEvent();
	event.pageName = "event_page_name";
	event.pageType = "event_page_type";
	event.items = [tc_item_1];
	event.addAdditionalPropertyWithIntValue("key_additional_1", 12);
	event.addAdditionalPropertyWithListValue("key_additional_2", [12,12,12]);
	event.addAdditionalPropertyWithMapValue("key_map", {'test': 12, "test2": "value"});
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "view_item",
        "value": 8.00,
        "currency": "EUR",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ]
                }
            }
        ]
}
```
{% endtab %}
{% endtabs %}

## view\_item\_list

Log this event when the user has been presented with a list of items of a certain category.

#### Parameters <a href="#parameters_35" id="parameters_35"></a>

<table><thead><tr><th width="195">Name</th><th width="100">Type</th><th width="78">Required</th><th width="163">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>item_list_name</code></td><td><code>string</code></td><td>No</td><td>Related products</td><td>The name of the list in which the item was presented to the user.</td></tr><tr><td><code>user</code></td><td><a href="./#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="./#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```kotlin
cact('trigger','view_item_list', {
  item_list_name: 'Related products',
   items: [{
    id: 'SKU_12345',
    quantity: 1,
    price: 9.99,
    variant: 'red',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12345',
      name: 'Trex tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'boy',
      brand: 'Lacoste',
      colors: ['red'],
      price: 9.99
    }
  }, {
    id: 'SKU_12346',
    quantity: 1,
    price: 9.99,
    variant: 'green',
    coupon: 'CHRISTMAS',
    discount: 1.99,
    product:{
      id: '12346',
      name: 'Heart tshirt',
      category_1: 'clothes',
      category_2: 't-shirts',
      category_3: 'girl',
      brand: 'Jenny',
      colors: ['blue','white'],
      price: 9.99
    }
  }],
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val item1 = TCItem("my_product1_id", TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1)
val item2 = TCItem("my_product2_id", TCProduct("my_product_2_id", "my_product_2_name", 110f), 1)
val items = listOf<TCItem>(item1, item2)

val event = TCViewItemList(items)
    event.itemListName = "your products"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
TCItem item1 = new TCItem("my_product1_id", new TCProduct("my_product_1_id", "my_product_1_name", 12.5f), 1);
TCItem item2 = new TCItem("my_product2_id", new TCProduct("my_product_2_id", "my_product_2_name", 25.6f), 1);
ArrayList<TCItem> items = new ArrayList<>(Arrays.asList(item1, item2));

TCViewItemListEvent event = new TCViewItemListEvent(items);
event.itemListName = "your products";
serverside.execute(event);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
NSMutableArray *items = [[NSMutableArray alloc] init];
[items addObject: [[TCItem alloc] initWithItemId: @"iID1"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID1" 
                                  withName: @"pName1" 
                                  withPrice: @1.5f]
                                  withQuantity: 1]];
[items addObject: [[TCItem alloc] initWithItemId: @"iID2"
                                  withProduct: [[TCProduct alloc] initWithProductId: @"pID2" 
                                  withName: @"pName2" 
                                  withPrice: [[NSDecimalNumber alloc] initWithFloat: 2.5f]]
                                  withQuantity: 2]];

TCViewItemListEvent *event = [[TCViewItemListEvent alloc] initWithItems: items];
event.itemListName = @"summer_collection";

[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let item_1:TCItem = TCItem(itemId: "my_item1.id", with: TCProduct(productId: "my_product1.id", withName: "my_product1.name", withPrice: 12.5), withQuantity: 1)
let item_2:TCItem = TCItem(itemId: "my_item2.id", with: TCProduct(productId: "my_product2.id", withName: "my_product2.name", withPrice: 22.5), withQuantity: 1)

let event = TCViewItemListEvent(items: [item_1, item_2])
	event?.itemListName = "summer_collection"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
TCProduct tc_product = TCProduct();
		tc_product.ID = "product_1_ID";
		tc_product.name = "product_1_name";
		tc_product.price = 150;
		tc_product.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_1 = TCItem();
		tc_item_1.ID = "item_1_id";
		tc_item_1.product = tc_product;
		tc_item_1.quantity = 1;
		tc_item_1.addAdditionalProperty("key_additional_item", "val_additional_product");
TCProduct tc_product_2 = TCProduct();
		tc_product_2.ID = "product_2_ID";
		tc_product_2.name = "product_2_name";
		tc_product_2.price = 150;
		tc_product_2.addAdditionalProperty("key_additional_product", "val_additional_product");
TCItem tc_item_2 = TCItem();
		tc_item_2.ID = "item_2_id";
		tc_item_2.quantity = 2;
		tc_item_2.product = tc_product;
		tc_item_2.addAdditionalProperty("key_additional_item", "val_additional_product");

var event = TCViewItemListEvent();
	event.pageName = "event_page_name";
	event.pageType = "event_page_type";
	event.items = [tc_item_1, tc_item_2];
	event.addAdditionalPropertyWithIntValue("key_additional_1", 12);
	event.addAdditionalPropertyWithListValue("key_additional_2", [12,12,12]);
	event.addAdditionalPropertyWithMapValue("key_map", {'test': 12, "test2": "value"});
	event.itemListName = "itemListName";	
serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
    "event_name": "view_item_list",
        "item_list_name": "Related products",
        "items": [
            {
                "id": "SKU_12345",
                "quantity": 1,
                "price": 9.99,
                "variant": "red",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12345",
                    "name": "Trex tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "boy",
                    "brand": "Lacoste",
                    "colors": [
                        "red"
                    ],
                    "price": 9.99
                }
            },
            {
                "id": "SKU_12346",
                "quantity": 1,
                "price": 9.99,
                "variant": "green",
                "coupon": "CHRISTMAS",
                "discount": 1.99,
                "product": {
                    "id": "12346",
                    "name": "Heart tshirt",
                    "category_1": "clothes",
                    "category_2": "t-shirts",
                    "category_3": "girl",
                    "brand": "Jenyfion",
                    "colors": [
                        "blue",
                        "white"
                    ],
                    "price": 9.99
                }
            }
        ],
        "user": {
            "id": "12345",
            "email": "toto@domain.fr",
            "consent_categories": [
                1,
                3
            ]
        }
}
```
{% endtab %}
{% endtabs %}

## - COMMON SCHEMAS -

### Item

#### Parameters **(required and recommended)** <a href="#parameters_27" id="parameters_27"></a>

<table><thead><tr><th width="179">Name</th><th>Type</th><th width="64">Required</th><th width="129">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>SKU_12345</td><td><p>The ID of an item.</p><p>If you don't have an item id, you can use the product id as value. This field is used as key for updates (ex : refund)</p></td></tr><tr><td><code>product</code></td><td><a href="./#product"><code>Object&#x3C;Product></code></a></td><td><strong>Yes</strong></td><td></td><td>The product details</td></tr><tr><td><code>variant</code></td><td><code>string</code></td><td>No</td><td>red</td><td>The variant of the item.</td></tr><tr><td><code>list_position</code></td><td><code>number</code></td><td>No</td><td>1</td><td>The item's position in a list or collection.</td></tr><tr><td><code>discount</code></td><td><code>number</code></td><td>No</td><td>2.00</td><td>Monetary value of discount for one current item</td></tr><tr><td><code>quantity</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>2</td><td>The quantity of the item.</td></tr><tr><td><code>affiliation</code></td><td><code>string</code></td><td><strong>No</strong>*</td><td>DOWNLOAD</td><td>Required for most affiliation's destination.</td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>The coupon code associated with an item.</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>0</td><td>The final price of items (taxes <strong>included</strong>). It corresponds to the unit price tax included  * quantity of the items</td></tr><tr><td><code>cancelled_value</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Amount of<br>cancelled items<br>(taxes <strong>included</strong>)</td></tr><tr><td><code>cancelled_quantity</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Quantity of cancelled items (taxes <strong>included</strong>)</td></tr><tr><td><code>original_value</code></td><td><code>number</code></td><td>No</td><td>10.00</td><td>Original price for the item (taxes <strong>included</strong>)</td></tr><tr><td><code>returned_value</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Item returned price (taxes <strong>included</strong>)</td></tr><tr><td><code>returned_quantity</code></td><td><code>number</code></td><td>No</td><td>0</td><td>Items quantity returned</td></tr></tbody></table>

### Product

**Parameters (required and recommended)**

<table><thead><tr><th width="133">Name</th><th>Type</th><th width="76">Required</th><th>Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td><strong>Yes</strong>*</td><td>12345</td><td><p>The ID of the product (ex: in your product catalog database)<br>The <code>item.id</code> and <code>product.id</code> do not have to be different. If they are different, typically the <code>product.id</code> is a database identifier, like <code>9714107479</code> and the <code>item.id</code> is a public-facing identifier like <code>SKU-12345</code>.</p><p>(*) If you have imported your product's catalog in the platform, the <code>product.id</code> corresponds to the unique product id in the catalog and can be used with id expansion feature.</p></td></tr><tr><td><code>name</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>Trex</td><td>Product name</td></tr><tr><td><code>price</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>14.99</td><td>The price of the product (with discount and taxes <strong>excluded)</strong></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the <code>price</code>, in 3-letter ISO 4217 format.</p><p>If set, event-level <code>currency</code> is ignored.<br><br>Multiple currencies per event is not supported. Each item should set the same currency.</p></td></tr><tr><td><code>category_1</code></td><td><code>string</code></td><td>No</td><td>T-Shirts</td><td>Product Category (context-specific). <code>item_category2</code> through <code>item_category5</code> can also be used if the product has many categories.</td></tr><tr><td><code>brand</code></td><td><code>string</code></td><td>No</td><td>Lacoste</td><td>Product brand</td></tr><tr><td><code>colors</code></td><td><code>Array[string]</code></td><td>No</td><td>[blue, white]</td><td>The color(s) of the product</td></tr><tr><td><code>size</code></td><td><code>string</code></td><td>No</td><td>128</td><td>Size of the article</td></tr></tbody></table>

### User

When you send an event, it needs to carry enough information to identify which user made it. We can link events together using cookies. But destination partners require accurate identifiers to take actions.

`id` and `email` are usually the most useful parameters. Though some destination partners also use `firstname`, `lastname`, `birthdate`, `city`, ...

You won't always have all of those parameters. But it is recommended to send them as soon as you can during user's browsing.

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="173">Name</th><th width="121">Type</th><th width="91">Required</th><th>Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td>No*</td><td>845454</td><td><p>User's main identifier (e.g. CRM id)</p><p>(*) required for many destinations and internal processing.</p></td></tr><tr><td><code>email</code></td><td><code>string</code></td><td>Yes*</td><td>john.doe@example.com</td><td><p>Email (plain value)</p><p>(*) required for many destinations and internal processing. Not required if <code>email_sha256</code> is provided</p></td></tr><tr><td><code>email_md5</code></td><td><code>string</code></td><td>No*</td><td>8eb1b52... (size 32)</td><td>Email, hashed using <a href="https://en.wikipedia.org/wiki/MD5">MD5 algorithm</a>. Not required if <code>email</code> is provided (see below)</td></tr><tr><td><code>email_sha256</code></td><td><code>string</code></td><td>No*</td><td>836f82d... (size 64)</td><td>Email, hashed using <a href="https://en.wikipedia.org/wiki/SHA-2">SHA-256 algorithm</a>. Not required if <code>email</code> is provided (see below)</td></tr><tr><td><code>phone</code></td><td><code>string</code></td><td>No*</td><td>+33612345678</td><td>Phone number, <a href="https://en.wikipedia.org/wiki/E.164">E.164</a> format<br>(*) required for some destinations.</td></tr><tr><td><code>firstname</code></td><td><code>string</code></td><td>No</td><td>John</td><td>First name</td></tr><tr><td><code>lastname</code></td><td><code>string</code></td><td>No</td><td>Doe</td><td>Last name</td></tr><tr><td><code>gender</code></td><td><code>string</code></td><td>No</td><td>m</td><td><p>Gender</p><ul><li><code>f</code> for Female</li><li><code>m</code> for Male</li></ul></td></tr><tr><td><code>birthdate</code></td><td><code>string</code></td><td>No</td><td>1970-01-01</td><td>Birth date, <code>YYYY-MM-DD</code> format</td></tr><tr><td><code>city</code></td><td><code>string</code></td><td>No</td><td>Boston</td><td>City</td></tr><tr><td><code>state</code></td><td><code>string</code></td><td>No</td><td>Massachusetts</td><td>State</td></tr><tr><td><code>street</code></td><td><code>string</code></td><td>No</td><td>303 Sumner St</td><td>Street address</td></tr><tr><td><code>zipcode</code></td><td><code>string</code></td><td>No</td><td>02108</td><td>Zip code</td></tr><tr><td><code>country</code></td><td><code>string</code></td><td>No</td><td>USA</td><td>Country code, ISO 3166-1 <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">2-letter</a> or <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3">3-letter</a> formats</td></tr><tr><td><code>consent_categories</code></td><td><code>Array</code></td><td><strong>Yes</strong></td><td>[1,3,4]</td><td>User's consent categories. It should contain only the categories where the user has given his consent.<br>Necessary to grant data sharing with destination partners. It is automatically filled from web sources if you use Commanders Act CMP.</td></tr><tr><td>status</td><td><code>string</code></td><td>No</td><td>New</td><td>Status as reported in your CRM (E.g. "New", "Existing", "Premium")</td></tr></tbody></table>

**About Hashing**

In some cases, you won't be able to send a parameter **plain** value. It is either unavailable or restricted.

Thus it might be possible to send the **hashed** values. We currently accept 2 algorithm : [`md5`](https://en.wikipedia.org/wiki/MD5) and [`sha256`](https://en.wikipedia.org/wiki/SHA-2).

Every `user.<property>` can be sent under hashed format with algorithm suffix: `_md5` or `_sha256` _(underscore followed by lowercase algorithm name)_

Example :

```
{
  user: {
    email_md5: '8eb1b522f60d11fa897de1dc6351b7e8',                                      // md5('john.doe@example.com')
    email_sha256: '836f82db99121b3481011f16b49dfa5fbc714a0d1b1b9f784a1ebbbf5b39577f',   // sha256('john.doe@example.com')
    phone_md5: '60dd761f55cb17f0532c9fb1679e8ddd',                                      // md5('+33612345678')
    phone_sha256: '42d573cfc315801d4cd8eddd5416b416a0bf298b9b9e12d6b07442c91db42bd8',   // sha256('+33612345678')
  }
}
```

> :information\_source: we only support hex (base16) encoding\
> &#xNAN;_(i.e.: **hashed** values are carried by strings with \[0-9a-f] characters)_\
> Other encodings are not supported yet

No need to send both **plain** and **hashed** values :

* if you send **plain** value, the **hashed** values aren't necessary\
  &#xNAN;_&#x57;e can generate **hashed** values on server side using **plain** value_
* if you don't send **plain** value, then you should fill as much **hashed** values as possible\
  &#xNAN;_&#x50;artners require different hash algorithms and without **plain** value, we can't generate any hash. That's why we need the exact **hashed** value_

## - ENUMERATED VALUE -

### Payment methods

Enumerated Values for payment methods :

| Property        | Value                           |
| --------------- | ------------------------------- |
| payment\_method | by\_invoice                     |
| payment\_method | by\_bank\_transfer\_in\_advance |
| payment\_method | card                            |
| payment\_method | check\_in\_advance              |
| payment\_method | cod                             |
| payment\_method | coupon                          |
| payment\_method | direct\_debit                   |
| payment\_method | online\_payment\_system         |
| payment\_method | other                           |

### Purchase status

Enumerated Values for purchase status:

<table><thead><tr><th width="380">Property</th><th>Value</th></tr></thead><tbody><tr><td>status</td><td>canceled</td></tr><tr><td>status</td><td>delivered</td></tr><tr><td>status</td><td>in_progress</td></tr><tr><td>status</td><td>partially_delivered</td></tr><tr><td>status</td><td>partially_returned</td></tr><tr><td>status</td><td>partially_shipped</td></tr><tr><td>status</td><td>pending_shipment</td></tr><tr><td>status</td><td>returned</td></tr><tr><td>status</td><td>shipped</td></tr><tr><td>status</td><td>pending</td></tr></tbody></table>



##



###

