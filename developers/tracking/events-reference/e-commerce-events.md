# E-commerce events

## add\_payment\_info <a href="#add_payment_info" id="add_payment_info"></a>

This event signifies a user has submitted their payment information

**Parameters (required and recommended)**

<table><thead><tr><th width="137">Name</th><th width="101">Type</th><th width="76">Required</th><th width="147">Example Value</th><th width="288">Description</th></tr></thead><tbody><tr><td><code>payment_method</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>card</td><td>The chosen method of payment (see list of possible values below)</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list and is mandatory to manage consents. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>revenue</code></td><td><code>number</code></td><td>No</td><td>16.00</td><td><p>Revenue (shipping price and taxes <strong>excluded</strong>) after discount.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td>No</td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

```javascript
cact('trigger','add_payment_info', {
  payment_method: 'card',
  revenue: 16.00,
  value: 22.53,
  currency: 'EUR'
});
```

## add\_shipping\_info

This event signifies a user has submitted their shipping information.

#### Parameters <a href="#parameters_2" id="parameters_2"></a>

<table><thead><tr><th width="138">Name</th><th width="99">Type</th><th width="74">Required</th><th width="159">Example value</th><th width="281">Description</th></tr></thead><tbody><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>Yes</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> or <code>value</code>parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>value</code></td><td><code>number</code></td><td>Yes</td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>shipping_tier</code></td><td><code>string</code></td><td>No</td><td>Ground</td><td>The shipping tier (e.g. <code>Next-day</code>, Air`) selected for delivery of the purchased item.</td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

## add\_to\_cart

This event signifies that an item was added to a cart for purchase.

**Parameters (required and recommended)**

<table><thead><tr><th width="136">Name</th><th width="103">Type</th><th width="102">Required</th><th width="135">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong>*</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong>*</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

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
  }]
});
```

## add\_to\_wishlist

The event signifies that an item was added to a wishlist. Use this event to identify popular gift items in your app.

**Parameters (required and recommended)**

<table><thead><tr><th width="142">Name</th><th width="100">Type</th><th width="80">Required</th><th width="157">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

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
  }]
});
```

## begin\_checkout <a href="#begin_checkout" id="begin_checkout"></a>

This event signifies that a user has begun a checkout.

**Parameters (required and recommended)**

<table><thead><tr><th width="138">Name</th><th width="98">Type</th><th width="78">Required</th><th width="157">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>16.00</td><td>The monetary value of the event (shipping price and taxes <strong>excluded</strong>) after discount</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong></td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

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

## generate\_lead <a href="#generate_lead" id="generate_lead"></a>

Log this event when a lead has been generated to understand the efficacy of your re-engagement campaigns.

**Parameters (required and recommended)**

<table><thead><tr><th width="134">Name</th><th width="103">Type</th><th width="77">Required</th><th width="144">Example Value</th><th width="288">Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td><strong>No</strong>*</td><td>9.99</td><td><p>The monetary value of the event.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>No*</strong></td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>id</code></td><td><code>string</code></td><td>No</td><td></td><td>Lead id</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

```javascript
cact('trigger','generate_lead', {
  currency: 'EUR',
  value: 9.99,
  id: 'L_12345'
});
```

## purchase

Fire this event when one or more items are purchased by a user.

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="160">Name</th><th width="99">Type</th><th width="80">Required</th><th width="157">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>O_1245</td><td>Transaction id. Used as key for updates</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td><strong>Yes</strong></td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p>All properties that you add here will be used as conditions for matching users in our database.</p><p><code>cosent_categories</code> is automatically filled if you use Commanders Act CMP.</p></td></tr><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>16.00</td><td>The monetary value of the event (shipping price and taxes <strong>excluded</strong>) after discount</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>shipping_amount</code></td><td><code>number</code></td><td>No</td><td>3.33</td><td>Shipping cost associated with a transaction.</td></tr><tr><td><code>tax_amount</code></td><td><code>number</code></td><td>No</td><td>3.20</td><td>Tax associated with a transaction.</td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong></td><td>EUR</td><td>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>type</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>offline</td><td>Type of conversion (online, offline, call etc.)</td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr><tr><td><code>payment_method</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>card</td><td>Payment method type (see list of <a href="e-commerce-events.md#payment-methods">possible values</a> below)</td></tr><tr><td><code>status</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>in_progress</td><td>Status of the conversion (see list of <a href="e-commerce-events.md#purchase-status">possible values</a> below).<br><em>Conversions with status "pending" are not included in default sum and counts aggregated on augmented user attributes feature</em></td></tr><tr><td><code>last_channel</code></td><td><code>string</code></td><td>No</td><td>display</td><td>The last channel just before the purchase.</td></tr><tr><td><code>last_source</code></td><td><code>string</code></td><td>No</td><td>google.com</td><td>The last source (referrer) just before the purchase.</td></tr></tbody></table>

**Automatically added by cact API**

| Name  | Type        | Required | Example | Description                                                                                   |
| ----- | ----------- | -------- | ------- | --------------------------------------------------------------------------------------------- |
| `url` | string(url) | No       | none    | <p>URL to the website where you can buy the item</p><p>Equivalent to window.location.href</p> |

**Example**

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

## refund

Fire this event when a purchase was refund

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="182">Name</th><th width="99">Type</th><th width="76">Required</th><th width="154">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>O_1245</td><td>Transaction id. Used as key for updates</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p>All properties that you add here will be used as conditions for matching users in our database.</p><p><code>cosent_categories</code> is automatically filled if you use Commanders Act CMP.</p></td></tr><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>16.00</td><td>The monetary value of the event (shipping price and taxes <strong>excluded</strong>) after discount</td></tr><tr><td><code>value</code></td><td><code>number</code></td><td><strong>Yes</strong></td><td>22.53</td><td>The monetary value of the event (shipping price and taxes <strong>included</strong>) after discount</td></tr><tr><td><code>shipping_amount</code></td><td><code>number</code></td><td>No</td><td>3.33</td><td>Shipping cost associated with a transaction.</td></tr><tr><td><code>tax_amount</code></td><td><code>number</code></td><td>No</td><td>3.20</td><td>Shipping cost associated with a transaction.</td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes</strong></td><td>EUR</td><td>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</td></tr><tr><td><code>coupon</code></td><td><code>string</code></td><td>No</td><td>CHRISTMAS</td><td>Coupon code used for a purchase.</td></tr><tr><td><code>type</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>offline</td><td>Type of conversion (online, offline, call etc.)</td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td>No*</td><td></td><td>(*) <code>items</code> is required for partial refunds but it can be omitted for full refunds.</td></tr></tbody></table>

**Automatically added by cact API**

<table><thead><tr><th width="128">Name</th><th width="115">Type</th><th width="103">Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td><code>url</code></td><td>string(url)</td><td>No</td><td>none</td><td><p>URL to the website where you can buy the item</p><p>Equivalent to window.location.href</p></td></tr></tbody></table>

**Example**

```javascript
cact('trigger','refund', {
  id: 'O_12345',
  coupon: 'CHRISTMAS',
  revenue: 16.00,
  value: 20.33,
  shipping_amount: 3.33,
  tax_amount: 3.20,
  currency: 'EUR'
})
```

## remove\_from\_cart

This event signifies that an item was removed from a cart.

**Parameters (required and recommended)**

<table><thead><tr><th width="146">Name</th><th width="103">Type</th><th width="106">Required</th><th>Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

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
  }]
});
```

## select\_item

This event signifies an item was selected from a list.

#### Parameters <a href="#parameters_23" id="parameters_23"></a>

<table><thead><tr><th width="192">Name</th><th width="105">Type</th><th width="71">Required</th><th width="118">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>item_list_name</code></td><td><code>string</code></td><td>No</td><td>Related products</td><td>The name of the list in which the item was presented to the user.</td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event. The <code>items</code> array is expected to have a single element, representing the selected item.</td></tr></tbody></table>

**Example**

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
  }]
});
```

## view\_cart

This event signifies that a user viewed their cart.

**Parameters (required and recommended)**

<table><thead><tr><th width="147">Name</th><th width="102">Type</th><th width="76">Required</th><th width="163">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>value</code></td><td><code>number</code></td><td>No</td><td>8.00</td><td><p>The monetary value of the event.<br>(<em>)<code>value</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>value</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td>No</td><td>EUR</td><td><p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p></td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

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
  }]
});
```

## view\_item

This event signifies that some content was shown to the user. Use this event to manage the most popular items viewed.

**Parameters (required and recommended)**

<table><thead><tr><th width="139">Name</th><th width="101">Type</th><th width="82">Required</th><th width="157">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>revenue</code></td><td><code>number</code></td><td><strong>Yes</strong>*</td><td>9.99</td><td><p>The monetary value of the event.<br>(<em>)<code>revenue</code> is typically required for meaningful reporting.</em></p><p><em>(</em>)<code>currency</code> is required if you set <code>revenue</code>.</p></td></tr><tr><td><code>currency</code></td><td><code>string (ISO 4217)</code></td><td><strong>Yes*</strong></td><td>EUR</td><td>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

## view\_item\_list

Log this event when the user has been presented with a list of items of a certain category.

#### Parameters <a href="#parameters_35" id="parameters_35"></a>

<table><thead><tr><th width="195">Name</th><th width="100">Type</th><th width="78">Required</th><th width="163">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>item_list_name</code></td><td><code>string</code></td><td>No</td><td>Related products</td><td>The name of the list in which the item was presented to the user.</td></tr><tr><td><code>user</code></td><td><a href="e-commerce-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>items</code></td><td><a href="e-commerce-events.md#item"><code>Array&#x3C;Item></code></a></td><td><strong>Yes</strong></td><td></td><td>The items for the event.</td></tr></tbody></table>

**Example**

```javascript
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
      brand: 'Jenyfion',
      colors: ['blue','white'],
      price: 9.99
    }
  }]
});
```

## - COMMON SCHEMAS -

### Item

#### Parameters **(required and recommended)** <a href="#parameters_27" id="parameters_27"></a>

| Name            | Type                                              | Required | Example Value | Description                                                                                                                                            |
| --------------- | ------------------------------------------------- | -------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`            | `string`                                          | **Yes**  | SKU\_12345    | <p>The ID of an item.</p><p>If you don't have an item id, you can use the product id as value. This field is used as key for updates (ex : refund)</p> |
| `product`       | [`Object<Product>`](e-commerce-events.md#product) | **Yes**  |               | The product details                                                                                                                                    |
| `variant`       | `string`                                          | No       | red           | The variant of the item.                                                                                                                               |
| `list_position` | `number`                                          | No       | 1             | The item's position in a list or collection.                                                                                                           |
| `discount`      | `number`                                          | No       | 2.00          | Monetary value of discount associated with a purchase                                                                                                  |
| `quantity`      | `number`                                          | **Yes**  | 2             | The quantity of the item.                                                                                                                              |
| `affiliation`   | `string`                                          | **No**\* | DOWNLOAD      | Required for most affiliation's destination.                                                                                                           |
| `coupon`        | `string`                                          | No       | CHRISTMAS     | The coupon code associated with an item.                                                                                                               |

### Product

**Parameters (required and recommended)**

| Name         | Type                | Required  | Example Value  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------ | ------------------- | --------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`         | `string`            | **Yes**\* | 12345          | <p>The ID of the product (ex: in your product catalog database)<br>The <code>item.id</code> and <code>product.id</code> do not have to be different. If they are different, typically the <code>product.id</code> is a database identifier, like <code>9714107479</code> and the <code>item.id</code> is a public-facing identifier like <code>SKU-12345</code>.</p><p>(*) If you have imported your product's catalog in the platform, the <code>product.id</code> corresponds to the unique product id in the catalog and can be used with id expansion feature.</p> |
| `name`       | `string`            | **Yes**   | Trex           | Product name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `price`      | `number`            | **Yes**   | 14.99          | The price of the product                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `currency`   | `string (ISO 4217)` | No        | EUR            | <p>Currency of the <code>price</code>, in 3-letter ISO 4217 format.</p><p>If set, event-level <code>currency</code> is ignored.<br><br>Multiple currencies per event is not supported. Each item should set the same currency.</p>                                                                                                                                                                                                                                                                                                                                     |
| `category_1` | `string`            | No        | T-Shirts       | Product Category (context-specific). `item_category2` through `item_category5` can also be used if the product has many categories.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `brand`      | `string`            | No        | Lacoste        | Product brand                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `colors`     | `Array[string]`     | No        | \[blue, white] | The color(s) of the product                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `size`       | `string`            | No        | 128            | Size of the article                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

### User

When you send an event, it needs to carry enough information to identify which user made it. We can link events together using cookies. But destination partners require accurate identifiers to take actions.

`id` and `email` are usually the most useful parameters. Though some destination partners also use `firstname`, `lastname`, `birthdate`, `city`, ...

You won't always have all of those parameters. But it is recommended to send them as soon as you can during user's browsing.

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="229">Name</th><th width="118">Type</th><th width="104">Required</th><th>Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td>No*</td><td>845454</td><td><p>User's main identifier (e.g. CRM id)</p><p>(*) required for many destinations and internal processing.</p></td></tr><tr><td><code>email</code></td><td><code>string</code></td><td>Yes*</td><td>john.doe@example.com</td><td><p>Email (plain value)</p><p>(*) required for many destinations and internal processing. Not required if <code>email_sha256</code> is provided</p></td></tr><tr><td><code>email_md5</code></td><td><code>string</code></td><td>No*</td><td>8eb1b52... (size 32)</td><td>Email, hashed using <a href="https://en.wikipedia.org/wiki/MD5">MD5 algorithm</a>. Not required if <code>email</code> is provided (see below)</td></tr><tr><td><code>email_sha256</code></td><td><code>string</code></td><td>No*</td><td>836f82d... (size 64)</td><td>Email, hashed using <a href="https://en.wikipedia.org/wiki/SHA-2">SHA-256 algorithm</a>. Not required if <code>email</code> is provided (see below)</td></tr><tr><td><code>phone</code></td><td><code>string</code></td><td>No*</td><td>+33612345678</td><td>Phone number, <a href="https://en.wikipedia.org/wiki/E.164">E.164</a> format<br>(*) required for some destinations.</td></tr><tr><td><code>firstname</code></td><td><code>string</code></td><td>No</td><td>John</td><td>First name</td></tr><tr><td><code>lastname</code></td><td><code>string</code></td><td>No</td><td>Doe</td><td>Last name</td></tr><tr><td><code>gender</code></td><td><code>string</code></td><td>No</td><td>m</td><td><p>Gender</p><ul><li><code>f</code> for Female</li><li><code>m</code> for Male</li></ul></td></tr><tr><td><code>birthdate</code></td><td><code>string</code></td><td>No</td><td>1970-01-01</td><td>Birth date, <code>YYYY-MM-DD</code> format</td></tr><tr><td><code>city</code></td><td><code>string</code></td><td>No</td><td>Boston</td><td>City</td></tr><tr><td><code>state</code></td><td><code>string</code></td><td>No</td><td>Massachusetts</td><td>State</td></tr><tr><td><code>zipcode</code></td><td><code>string</code></td><td>No</td><td>02108</td><td>Zip code</td></tr><tr><td><code>country</code></td><td><code>string</code></td><td>No</td><td>USA</td><td>Country code, ISO 3166-1 <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">2-letter</a> or <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3">3-letter</a> formats</td></tr><tr><td><code>consent_categories</code></td><td><code>Array</code></td><td><strong>Yes</strong></td><td>[1,2,3]</td><td>User's consent categories.<br>Necessary to grant data sharing with destination partners. It is automatically filled from web sources if you use Commanders Act CMP.</td></tr></tbody></table>

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
> _(i.e.: **hashed** values are carried by strings with \[0-9a-f] characters)_\
> Other encodings are not supported yet

No need to send both **plain** and **hashed** values :

* if you send **plain** value, the **hashed** values aren't necessary\
  _We can generate **hashed** values on server side using **plain** value_
* if you don't send **plain** value, then you should fill as much **hashed** values as possible\
  _Partners require different hash algorithms and without **plain** value, we can't generate any hash. That's why we need the exact **hashed** value_



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

