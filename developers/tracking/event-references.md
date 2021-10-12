# Events reference

## add\_payment\_info <a id="add_payment_info"></a>

This event signifies a user has submitted their payment information

**Parameters \(required and recommended\)**

<table style="font-size:11px">
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>payment_method</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">card</td>
      <td style="text-align:left">The chosen method of payment (see list of possible values below)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>coupon</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">CHRISTMAS</td>
      <td style="text-align:left">Coupon code used for a purchase.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>revenue</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">16.00</td>
      <td style="text-align:left">
        <p>Revenue (shipping price and taxes <b>excluded</b>) after discount.
          <br />(*)<code>revenue</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

**Example**

```javascript
cact('trigger','add_payement_info', {
  payment_method: 'card',
  revenue: 16.00,
  value: 22.53,
  currency: 'EUR'
});
```

## add\_shipping\_info

This event signifies a user has submitted their shipping information.

#### Parameters <a id="parameters_2"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> or <code>value</code>parameter,
          you must also supply the <code>currency</code> parameter so revenue metrics
          can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">22.53</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>included</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>coupon</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">CHRISTMAS</td>
      <td style="text-align:left">Coupon code used for a purchase.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>shipping_tier</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Ground</td>
      <td style="text-align:left">The shipping tier (e.g. <code>Air</code>, <code>Next-day</code>) selected
        for delivery of the purchased item.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

## add\_to\_cart

This event signifies that an item was added to a cart for purchase.

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">8.00</td>
      <td style="text-align:left">
        <p>The monetary value of the event.
          <br />(*)<code>revenue</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

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

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">8.00</td>
      <td style="text-align:left">
        <p>The monetary value of the event.
          <br />(*)<code>revenue</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

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

## begin\_checkout <a id="begin_checkout"></a>

This event signifies that a user has begun a checkout.

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>revenue</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">16.00</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>excluded</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">22.53</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>included</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>coupon</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">CHRISTMAS</td>
      <td style="text-align:left">Coupon code used for a purchase.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

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

## generate\_lead <a id="generate_lead"></a>

Log this event when a lead has been generated to understand the efficacy of your re-engagement campaigns.

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>*</td>
      <td style="text-align:left">9.99</td>
      <td style="text-align:left">
        <p>The monetary value of the event.
          <br />(*)<code>revenue</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left"><b>Yes*</b>
      </td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Lead id</td>
    </tr>
  </tbody>
</table>

**Example**

```javascript
cact('trigger','generate_lead', {
  currency: 'EUR',
  valuz: 9.99,
  id: 'L_12345'
});
```

## login <a id="login"></a>

Send this event to signify that a user has logged in.

#### Parameters <a id="parameters_14"></a>

| Name | Type | Required | Example | Description |
| :--- | :--- | :--- | :--- | :--- |
| `method` | `string` | No | LinkedIn | The method used to login. |

**Example**

```javascript
cact('login', {
  method: 'LinkedIn'
});
```

## page\_view <a id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>type</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">product_list</td>
      <td style="text-align:left">
        <p>Page category. Recommanded predefined types:</p>
        <ul>
          <li>home</li>
          <li>landing</li>
          <li>product_list</li>
          <li>product</li>
          <li>content_list</li>
          <li>content</li>
          <li>search</li>
          <li>funnel</li>
          <li>success</li>
          <li>funnel_confirmation</li>
          <li>account</li>
          <li>cart</li>
          <li>legal (e.g. Privacy Policy)</li>
        </ul>
        <p>Equivalent to <code>tc_vars.env_template</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>name</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Suggestion for Mother&apos;s Day</td>
      <td style="text-align:left">Name of the page.</td>
    </tr>
  </tbody>
</table>

**Automatically added parameters by cact API**

| Name | Type | Required | Example Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| `title` | `number` | No | Products - MySite.com | Title of the page :[`document.title`](https://developer.mozilla.org/en-US/docs/Web/API/Document/title) from the DOM API |
| `url` | `string` | No | [http://www.mysite.com](http://www.mysite.com) | Full URL of the page. Equivalent to[`location.href`](https://developer.mozilla.org/en-US/docs/Web/API/Location) from the DOM API. |
| `path` | `string` | No | /products/mothers | Path portion of the URL of the page : [`location.pathname`](https://developer.mozilla.org/en-US/docs/Web/API/Location) from the DOM API. |
| `referrer` | `string` | No | [http://www.example.com](http://www.example.com) | Full URL of the previous page : [`document.referrer`](https://developer.mozilla.org/en-US/docs/Web/API/Document/referrer) from the DOM API. |

**Example**

```javascript
cact('trigger','page_view', {
  type: 'product_list', 
  name: 'Best sellers'
});
```

## purchase

Fire this event when one or more items are purchased by a user.

#### Parameters **\(required and recommended\)** <a id="parameters_17"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">O_1245</td>
      <td style="text-align:left">Transaction id. Used as key for updates</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>user</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#user"><code>Object&lt;User&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">
        <p><code>{<br />id: &apos;12345&apos;,<br />email: &apos;toto@domain.fr&apos;,</code>
        </p>
        <p><code>consent_categories: [1,3]</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
      <td style="text-align:left">
        <p>All properties that you add here will be used as conditions for matching
          users in our database.</p>
        <p><code>cosent_categories</code> is automatically filled if you use Commanders
          Act CMP.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>revenue</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">16.00</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>excluded</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">22.53</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>included</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>shipping_amount</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">3.33</td>
      <td style="text-align:left">Shipping cost associated with a transaction.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>tax_amount</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">3.20</td>
      <td style="text-align:left">Shipping cost associated with a transaction.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">Currency of the purchase or items associated with the event, in 3-letter
        ISO 4217 format.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>coupon</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">CHRISTMAS</td>
      <td style="text-align:left">Coupon code used for a purchase.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>type</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">offline</td>
      <td style="text-align:left">Type of conversion (online, offline, call etc.)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>payment_method</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">card</td>
      <td style="text-align:left">Payment method type (see list of <a href="events-reference.md#payment-methods">possible values</a> below)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>status</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">in_progress</td>
      <td style="text-align:left">Status of the conversion (see list of <a href="events-reference.md#purchase-status">possible values</a> below).
        <br
        /><em>Conversions with status &quot;pending&quot; are not included in default sum and counts aggregated on augmented user attributes feature</em>
      </td>
    </tr>
  </tbody>
</table>

**Automatically added by cact API**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>url</code>
      </td>
      <td style="text-align:left">string(url)</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">none</td>
      <td style="text-align:left">
        <p>URL to the website where you can buy the item</p>
        <p>Equivalent to window.location.href</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>consent_categories</code>
      </td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">[1,2,3]</td>
      <td style="text-align:left">Automatically added <b>only if </b>you use Commanders Act CMP (TrustCommander)</td>
    </tr>
  </tbody>
</table>

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

Fire this event when one or more items are purchased by a user.

#### Parameters **\(required and recommended\)** <a id="parameters_17"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">O_1245</td>
      <td style="text-align:left">Transaction id. Used as key for updates</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>user</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#user"><code>Object&lt;User&gt;</code></a>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">
        <p><code>{<br />id: &apos;12345&apos;,<br />email: &apos;toto@domain.fr&apos;,</code>
        </p>
        <p><code>consent_categories: [1,3]</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
      <td style="text-align:left">
        <p>All properties that you add here will be used as conditions for matching
          users in our database.</p>
        <p><code>cosent_categories</code> is automatically filled if you use Commanders
          Act CMP.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>revenue</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">16.00</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>excluded</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">22.53</td>
      <td style="text-align:left">The monetary value of the event (shipping price and taxes <b>included</b>)
        after discount</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>shipping_amount</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">3.33</td>
      <td style="text-align:left">Shipping cost associated with a transaction.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>tax_amount</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">3.20</td>
      <td style="text-align:left">Shipping cost associated with a transaction.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">Currency of the purchase or items associated with the event, in 3-letter
        ISO 4217 format.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>coupon</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">CHRISTMAS</td>
      <td style="text-align:left">Coupon code used for a purchase.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>type</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">offline</td>
      <td style="text-align:left">Type of conversion (online, offline, call etc.)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left">No*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">(*) <code>items</code> is required for partial refunds but it can be omitted
        for full refunds.</td>
    </tr>
  </tbody>
</table>

**Automatically added by cact API**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>url</code>
      </td>
      <td style="text-align:left">string(url)</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">none</td>
      <td style="text-align:left">
        <p>URL to the website where you can buy the item</p>
        <p>Equivalent to window.location.href</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>consent_categories</code>
      </td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">[1,2,3]</td>
      <td style="text-align:left">Automatically added <b>only if </b>you use Commanders Act CMP (TrustCommander)</td>
    </tr>
  </tbody>
</table>

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

## remove\_from\_to\_cart

This event signifies that an item was added to a cart for purchase.

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">8.00</td>
      <td style="text-align:left">
        <p>The monetary value of the event.
          <br />(*)<code>revenue</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

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

## search

Use this event to contextualize search operations. This event can help you identify the most popular content in your app.

#### Parameters <a id="parameters_21"></a>

| Name | Type | Required | Example value | Description |
| :--- | :--- | :--- | :--- | :--- |
| `search_term` | `string` | **Yes** | t-shirts | The term that was searched for. |

#### Example <a id="example_30"></a>

```javascript
cact('trigger','search', {
  search_term: 't-shirts'
});
```

## select\_content

This event signifies that a user has selected some content of a certain type. This event can help you identify popular content and categories of content in your app or click on internal promotion.

#### Parameters <a id="parameters_22"></a>

| Name | Type | Required | Example value | Description |
| :--- | :--- | :--- | :--- | :--- |
| `content_type` | `string` | No | product | The type of selected content. |
| `item_id` | `string` | No | I\_12345 | An identifier for the item that was selected. |

#### Example <a id="example_32"></a>

```javascript
cact('trigger','select_content', {
  content_type: 'product',
  item_id: 'I_12345'
});
```

## select\_item

This event signifies an item was selected from a list.

#### Parameters <a id="parameters_23"></a>

| Name | Type | Required | Example value | Description |
| :--- | :--- | :--- | :--- | :--- |
| `item_list_name` | `string` | No | Related products | The name of the list in which the item was presented to the user. |
| `items` | [`Array<Item>`](events-reference.md#item) | **Yes** |  | The items for the event. The `items` array is expected to have a single element, representing the selected item. |

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

## sign\_up <a id="sign_up"></a>

This event indicates that a user has signed up for an account.

#### Parameters **\(required and recommended\)** <a id="parameters_27"></a>

| Name | Type | Required | Example | Description |
| :--- | :--- | :--- | :--- | :--- |
| `method` | `string` | No | Facebook | The method used for sign up. |

**Example**

```javascript
cact('trigger','sign_up', {
  method: 'email'
});
```

## view\_cart

This event signifies that a user viewed their cart.

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>value</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">8.00</td>
      <td style="text-align:left">
        <p>The monetary value of the event.
          <br />(*)<code>value</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the purchase or items associated with the event, in 3-letter
          ISO 4217 format.</p>
        <p>(*) If you supply the <code>revenue</code> parameter, you must also supply
          the <code>currency</code> parameter so revenue metrics can be computed accurately.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

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

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>revenue</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>*</td>
      <td style="text-align:left">9.99</td>
      <td style="text-align:left">
        <p>The monetary value of the event.
          <br />(*)<code>revenue</code> is typically required for meaningful reporting.</p>
        <p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left"><b>Yes*</b>
      </td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">Currency of the purchase or items associated with the event, in 3-letter
        ISO 4217 format.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>items</code>
      </td>
      <td style="text-align:left"><a href="events-reference.md#item"><code>Array&lt;Item&gt;</code></a>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The items for the event.</td>
    </tr>
  </tbody>
</table>

## view\_item\_list

Log this event when the user has been presented with a list of items of a certain category.

#### Parameters <a id="parameters_35"></a>

| Name | Type | Required | Example value | Description |
| :--- | :--- | :--- | :--- | :--- |
| `item_list_name` | `string` | No | Related products | The name of the list in which the item was presented to the user. |
| `items` | [`Array<Item>`](events-reference.md#item) | **Yes** |  | The items for the event. |

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

## -  COMMON SCHEMAS -

### Item

#### Parameters **\(required and recommended\)** <a id="parameters_27"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">SKU_12345</td>
      <td style="text-align:left">
        <p>The ID of an item.</p>
        <p>If you don&apos;t have an item id, you can use the product id as value.
          This field is used as key for updates (ex : refund)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>product</code>
      </td>
      <td style="text-align:left">&lt;code&gt;&lt;/code&gt;<a href="events-reference.md#product"><code>Object&lt;Product&gt;</code></a>&lt;code&gt;&lt;/code&gt;</td>
      <td
      style="text-align:left"><b>Yes</b>
        </td>
        <td style="text-align:left"></td>
        <td style="text-align:left">The product details</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>variant</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">red</td>
      <td style="text-align:left">The variant of the item.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>list_position</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">The item&apos;s position in a list or collection.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>discount</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">2.00</td>
      <td style="text-align:left">Monetary value of discount associated with a purchase</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>quantity</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">The quantity of the item.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>coupon</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">CHRISTMAS</td>
      <td style="text-align:left">The coupon code associated with an item.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>custom</code>
      </td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Object containing custom properties you want to send</td>
    </tr>
  </tbody>
</table>

### Product

**Parameters \(required and recommended\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>*</td>
      <td style="text-align:left">12345</td>
      <td style="text-align:left">
        <p>The ID of the product (ex: in your product catalog database)
          <br />The <code>item.id</code> and <code>product.id</code> do not have to be different.
          If they are different, typically the <code>product.id</code> is a database
          identifier, like <code>9714107479</code> and the <code>item.id</code> is a
          public-facing identifier like <code>SKU-12345</code>.</p>
        <p>(*) If you have imported your product&apos;s catalog in the platform,
          the <code>product.id</code> corresponds to the unique product id in the catalog
          and can be used with id expansion feature.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>name</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">Trex</td>
      <td style="text-align:left">Product name</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>price</code>
      </td>
      <td style="text-align:left"><code>number</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">14.99</td>
      <td style="text-align:left">The price of the product</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left"><code>string (ISO 4217)</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">EUR</td>
      <td style="text-align:left">
        <p>Currency of the <code>price</code>, in 3-letter ISO 4217 format.</p>
        <p>If set, event-level <code>currency</code> is ignored.
          <br />
          <br />Multiple currencies per event is not supported. Each item should set the
          same currency.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>category_1</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">T-Shirts</td>
      <td style="text-align:left">Product Category (context-specific). <code>item_category2</code> through <code>item_category5</code> can
        also be used if the product has many categories.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>brand</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Lacoste</td>
      <td style="text-align:left">Product brand</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>colors</code>
      </td>
      <td style="text-align:left"><code>Array[string]</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">[blue, white]</td>
      <td style="text-align:left">The color(s) of the product</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>size</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">128</td>
      <td style="text-align:left">Size of the article</td>
    </tr>
  </tbody>
</table>

### User

#### Parameters **\(required and recommended\)** <a id="parameters_17"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Example Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>id</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Yes</b>
      </td>
      <td style="text-align:left">845454</td>
      <td style="text-align:left">User&apos;s id</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>email</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">Yes*</td>
      <td style="text-align:left">toto.domain.fr</td>
      <td style="text-align:left">User&apos;s email
        <br />(*)<code>email</code> or is required if <code>id</code> is not set</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>consent_categories</code>
      </td>
      <td style="text-align:left"><code>Array</code>
      </td>
      <td style="text-align:left">Yes*</td>
      <td style="text-align:left">[1,3,4]</td>
      <td style="text-align:left">
        <p>Consent categories of the user, to be allowed to share the event with
          partners.</p>
        <p>(*) Automatically filled if you use Commanders Act CMP</p>
      </td>
    </tr>
  </tbody>
</table>

## - ENUMERATED VALUE -

### Payment methods

Enumerated Values for payment methods :

| Property | Value |
| :--- | :--- |
| payment\_method | by\_invoice |
| payment\_method | by\_bank\_transfer\_in\_advance |
| payment\_method | card |
| payment\_method | check\_in\_advance |
| payment\_method | cod |
| payment\_method | coupon |
| payment\_method | direct\_debit |
| payment\_method | online\_payment\_system |
| payment\_method | other |

### Purchase status

Enumerated Values for purchase status:

| Property | Value |
| :--- | :--- |
| status | canceled |
| status | delivered |
| status | in\_progress |
| status | partially\_delivered |
| status | partially\_returned |
| status | partially\_shipped |
| status | pending\_shipment |
| status | returned |
| status | shipped |
| status | pending |
