# Event references

## add_payment_info <a href="add_payment_info" id="add_payment_info"></a>

This event signifies a user has submitted their payment information

**Parameters (required and recommended)**

| Name             | Type                                      | Required | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------------- | ----------------------------------------- | -------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `payment_method` | `string`                                  | **Yes**  | card          | The chosen method of payment (see list of possible values below)                                                                                                                                                                                                     |
| `coupon`         | `string`                                  | No       | CHRISTMAS     | Coupon code used for a purchase.                                                                                                                                                                                                                                     |
| `revenue`        | `number`                                  | No       | 16.00         | <p>Revenue (shipping price and taxes <strong>excluded</strong>) after discount.<br>(*)<code>revenue</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>                           |
| `currency`       | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `items`          | [`Array<Item>`](events-reference.md#item) | No       |               | The items for the event.                                                                                                                                                                                                                                             |

**Example**

```javascript
cact('trigger','add_payement_info', {
  payment_method: 'card',
  revenue: 16.00,
  value: 22.53,
  currency: 'EUR'
});
```

## add_shipping_info

This event signifies a user has submitted their shipping information.

#### Parameters <a href="parameters_2" id="parameters_2"></a>

| Name            | Type                                      | Required | Example value | Description                                                                                                                                                                                                                                                                               |
| --------------- | ----------------------------------------- | -------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `currency`      | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> or <code>value</code>parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `value`         | `number`                                  | No       | 22.53         | The monetary value of the event (shipping price and taxes **included**) after discount                                                                                                                                                                                                    |
| `coupon`        | `string`                                  | No       | CHRISTMAS     | Coupon code used for a purchase.                                                                                                                                                                                                                                                          |
| `shipping_tier` | `string`                                  | No       | Ground        | The shipping tier (e.g. `Air`, `Next-day`) selected for delivery of the purchased item.                                                                                                                                                                                                   |
| `items`         | [`Array<Item>`](events-reference.md#item) | **Yes**  |               | The items for the event.                                                                                                                                                                                                                                                                  |

## add_to_cart

This event signifies that an item was added to a cart for purchase.

**Parameters (required and recommended)**

| Name       | Type                                      | Required | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------- | ----------------------------------------- | -------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `value`    | `number`                                  | No       | 8.00          | <p>The monetary value of the event.<br>(*)<code>revenue</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>                                                                       |
| `currency` | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `items`    | [`Array<Item>`](events-reference.md#item) | **Yes**  |               | The items for the event.                                                                                                                                                                                                                                             |

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

## add_to_wishlist

The event signifies that an item was added to a wishlist. Use this event to identify popular gift items in your app.

**Parameters (required and recommended)**

| Name       | Type                                      | Required | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------- | ----------------------------------------- | -------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `value`    | `number`                                  | No       | 8.00          | <p>The monetary value of the event.<br>(*)<code>revenue</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>                                                                       |
| `currency` | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `items`    | [`Array<Item>`](events-reference.md#item) | **Yes**  |               | The items for the event.                                                                                                                                                                                                                                             |

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

## begin_checkout <a href="begin_checkout" id="begin_checkout"></a>

This event signifies that a user has begun a checkout.

**Parameters (required and recommended)**

| Name       | Type                                      | Required | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------- | ----------------------------------------- | -------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `revenue`  | `number`                                  | **Yes**  | 16.00         | The monetary value of the event (shipping price and taxes **excluded**) after discount                                                                                                                                                                               |
| `value`    | `number`                                  | **Yes**  | 22.53         | The monetary value of the event (shipping price and taxes **included**) after discount                                                                                                                                                                               |
| `currency` | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `coupon`   | `string`                                  | No       | CHRISTMAS     | Coupon code used for a purchase.                                                                                                                                                                                                                                     |
| `items`    | [`Array<Item>`](events-reference.md#item) | **Yes**  |               | The items for the event.                                                                                                                                                                                                                                             |

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

## generate_lead <a href="generate_lead" id="generate_lead"></a>

Log this event when a lead has been generated to understand the efficacy of your re-engagement campaigns.

**Parameters (required and recommended)**

| Name       | Type                | Required  | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------- | ------------------- | --------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `value`    | `number`            | **Yes**\* | 9.99          | <p>The monetary value of the event.<br>(*)<code>revenue</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>                                                                       |
| `currency` | `string (ISO 4217)` | **Yes\*** | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `id`       | `string`            | No        |               | Lead id                                                                                                                                                                                                                                                              |

**Example**

```javascript
cact('trigger','generate_lead', {
  currency: 'EUR',
  valuz: 9.99,
  id: 'L_12345'
});
```

## login <a href="login" id="login"></a>

Send this event to signify that a user has logged in.

#### Parameters <a href="parameters_14" id="parameters_14"></a>

| Name     | Type     | Required | Example  | Description               |
| -------- | -------- | -------- | -------- | ------------------------- |
| `method` | `string` | No       | LinkedIn | The method used to login. |

**Example**

```javascript
cact('login', {
  method: 'LinkedIn'
});
```

## page_view <a href="page_view" id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

**Parameters (required and recommended)**

| Name   | Type     | Required | Example Value               | Description                                                                                                                                                                                                                                                                                                                                                          |
| ------ | -------- | -------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type` | `string` | **Yes**  | product_list                | <p>Page category. Recommanded predefined types:</p><ul><li>home</li><li>landing</li><li>product_list</li><li>product</li><li>content_list</li><li>content</li><li>search</li><li>funnel</li><li>success</li><li>funnel_confirmation</li><li>account</li><li>cart</li><li>legal (e.g. Privacy Policy)</li></ul><p>Equivalent to <code>tc_vars.env_template</code></p> |
| `name` | `string` | No       | Suggestion for Mother's Day | Name of the page.                                                                                                                                                                                                                                                                                                                                                    |

**Automatically added parameters by cact API**

| Name       | Type     | Required | Example Value                                    | Description                                                                                                                                 |
| ---------- | -------- | -------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`    | `number` | No       | Products - MySite.com                            | Title of the page :[`document.title`](https://developer.mozilla.org/en-US/docs/Web/API/Document/title) from the DOM API                     |
| `url`      | `string` | No       | [http://www.mysite.com](http://www.mysite.com)   | Full URL of the page. Equivalent to[`location.href`](https://developer.mozilla.org/en-US/docs/Web/API/Location) from the DOM API.           |
| `path`     | `string` | No       | /products/mothers                                | Path portion of the URL of the page : [`location.pathname`](https://developer.mozilla.org/en-US/docs/Web/API/Location) from the DOM API.    |
| `referrer` | `string` | No       | [http://www.example.com](http://www.example.com) | Full URL of the previous page : [`document.referrer`](https://developer.mozilla.org/en-US/docs/Web/API/Document/referrer) from the DOM API. |

**Example**

```javascript
cact('trigger','page_view', {
  type: 'product_list', 
  name: 'Best sellers'
});
```

## purchase

Fire this event when one or more items are purchased by a user.

#### Parameters **(required and recommended)** <a href="parameters_17" id="parameters_17"></a>

| Name              | Type                                       | Required | Example                                                                                                                                                       | Description                                                                                                                                                                                                                                                     |
| ----------------- | ------------------------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`              | `string`                                   | **Yes**  | O\_1245                                                                                                                                                       | Transaction id. Used as key for updates                                                                                                                                                                                                                         |
| `user`            | [`Object<User>`](events-reference.md#user) | **Yes**  | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p>All properties that you add here will be used as conditions for matching users in our database.</p><p><code>cosent_categories</code> is automatically filled if you use Commanders Act CMP.</p>                                                              |
| `revenue`         | `number`                                   | **Yes**  | 16.00                                                                                                                                                         | The monetary value of the event (shipping price and taxes **excluded**) after discount                                                                                                                                                                          |
| `value`           | `number`                                   | **Yes**  | 22.53                                                                                                                                                         | The monetary value of the event (shipping price and taxes **included**) after discount                                                                                                                                                                          |
| `shipping_amount` | `number`                                   | No       | 3.33                                                                                                                                                          | Shipping cost associated with a transaction.                                                                                                                                                                                                                    |
| `tax_amount`      | `number`                                   | No       | 3.20                                                                                                                                                          | Shipping cost associated with a transaction.                                                                                                                                                                                                                    |
| `currency`        | `string (ISO 4217)`                        | **Yes**  | EUR                                                                                                                                                           | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.                                                                                                                                                                       |
| `coupon`          | `string`                                   | No       | CHRISTMAS                                                                                                                                                     | Coupon code used for a purchase.                                                                                                                                                                                                                                |
| `type`            | `string`                                   | Yes      | offline                                                                                                                                                       | Type of conversion (online, offline, call etc.)                                                                                                                                                                                                                 |
| `items`           | [`Array<Item>`](events-reference.md#item)  | Yes      |                                                                                                                                                               | The items for the event.                                                                                                                                                                                                                                        |
| `payment_method`  | `string`                                   | Yes      | card                                                                                                                                                          | Payment method type (see list of [possible values](events-reference.md#payment-methods) below)                                                                                                                                                                  |
| `status`          | `string`                                   | Yes      | in_progress                                                                                                                                                   | <p>Status of the conversion (see list of <a href="events-reference.md#purchase-status">possible values</a> below).<br><em>Conversions with status "pending" are not included in default sum and counts aggregated on augmented user attributes feature</em></p> |

**Automatically added by cact API**

| Name                 | Type        | Required | Example  | Description                                                                                   |
| -------------------- | ----------- | -------- | -------- | --------------------------------------------------------------------------------------------- |
| `url`                | string(url) | No       | none     | <p>URL to the website where you can buy the item</p><p>Equivalent to window.location.href</p> |
| `consent_categories` | Array       | No       | \[1,2,3] | Automatically added **only if **you use Commanders Act CMP (TrustCommander)                   |

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

#### Parameters **(required and recommended)** <a href="parameters_17" id="parameters_17"></a>

| Name              | Type                                       | Required | Example                                                                                                                                                       | Description                                                                                                                                                                                        |
| ----------------- | ------------------------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`              | `string`                                   | **Yes**  | O\_1245                                                                                                                                                       | Transaction id. Used as key for updates                                                                                                                                                            |
| `user`            | [`Object<User>`](events-reference.md#user) | No       | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p>All properties that you add here will be used as conditions for matching users in our database.</p><p><code>cosent_categories</code> is automatically filled if you use Commanders Act CMP.</p> |
| `revenue`         | `number`                                   | **Yes**  | 16.00                                                                                                                                                         | The monetary value of the event (shipping price and taxes **excluded**) after discount                                                                                                             |
| `value`           | `number`                                   | **Yes**  | 22.53                                                                                                                                                         | The monetary value of the event (shipping price and taxes **included**) after discount                                                                                                             |
| `shipping_amount` | `number`                                   | No       | 3.33                                                                                                                                                          | Shipping cost associated with a transaction.                                                                                                                                                       |
| `tax_amount`      | `number`                                   | No       | 3.20                                                                                                                                                          | Shipping cost associated with a transaction.                                                                                                                                                       |
| `currency`        | `string (ISO 4217)`                        | **Yes**  | EUR                                                                                                                                                           | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.                                                                                                          |
| `coupon`          | `string`                                   | No       | CHRISTMAS                                                                                                                                                     | Coupon code used for a purchase.                                                                                                                                                                   |
| `type`            | `string`                                   | Yes      | offline                                                                                                                                                       | Type of conversion (online, offline, call etc.)                                                                                                                                                    |
| `items`           | [`Array<Item>`](events-reference.md#item)  | No\*     |                                                                                                                                                               | (\*) `items` is required for partial refunds but it can be omitted for full refunds.                                                                                                               |

**Automatically added by cact API**

| Name                 | Type        | Required | Example  | Description                                                                                   |
| -------------------- | ----------- | -------- | -------- | --------------------------------------------------------------------------------------------- |
| `url`                | string(url) | No       | none     | <p>URL to the website where you can buy the item</p><p>Equivalent to window.location.href</p> |
| `consent_categories` | Array       | No       | \[1,2,3] | Automatically added **only if **you use Commanders Act CMP (TrustCommander)                   |

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

## remove_from_to_cart

This event signifies that an item was added to a cart for purchase.

**Parameters (required and recommended)**

| Name       | Type                                      | Required | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------- | ----------------------------------------- | -------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `value`    | `number`                                  | No       | 8.00          | <p>The monetary value of the event.<br>(*)<code>revenue</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>                                                                       |
| `currency` | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `items`    | [`Array<Item>`](events-reference.md#item) | **Yes**  |               | The items for the event.                                                                                                                                                                                                                                             |

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

#### Parameters <a href="parameters_21" id="parameters_21"></a>

| Name          | Type     | Required | Example value | Description                     |
| ------------- | -------- | -------- | ------------- | ------------------------------- |
| `search_term` | `string` | **Yes**  | t-shirts      | The term that was searched for. |

#### Example <a href="example_30" id="example_30"></a>

```javascript
cact('trigger','search', {
  search_term: 't-shirts'
});
```

## select_content

This event signifies that a user has selected some content of a certain type. This event can help you identify popular content and categories of content in your app or click on internal promotion.

#### Parameters <a href="parameters_22" id="parameters_22"></a>

| Name           | Type     | Required | Example value | Description                                   |
| -------------- | -------- | -------- | ------------- | --------------------------------------------- |
| `content_type` | `string` | No       | product       | The type of selected content.                 |
| `item_id`      | `string` | No       | I\_12345      | An identifier for the item that was selected. |

#### Example <a href="example_32" id="example_32"></a>

```javascript
cact('trigger','select_content', {
  content_type: 'product',
  item_id: 'I_12345'
});
```

## select_item

This event signifies an item was selected from a list.

#### Parameters <a href="parameters_23" id="parameters_23"></a>

| Name             | Type                                      | Required | Example value    | Description                                                                                                      |
| ---------------- | ----------------------------------------- | -------- | ---------------- | ---------------------------------------------------------------------------------------------------------------- |
| `item_list_name` | `string`                                  | No       | Related products | The name of the list in which the item was presented to the user.                                                |
| `items`          | [`Array<Item>`](events-reference.md#item) | **Yes**  |                  | The items for the event. The `items` array is expected to have a single element, representing the selected item. |

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

## sign_up <a href="sign_up" id="sign_up"></a>

This event indicates that a user has signed up for an account.

#### Parameters **(required and recommended)** <a href="parameters_27" id="parameters_27"></a>

| Name     | Type     | Required | Example  | Description                  |
| -------- | -------- | -------- | -------- | ---------------------------- |
| `method` | `string` | No       | Facebook | The method used for sign up. |

**Example**

```javascript
cact('trigger','sign_up', {
  method: 'email'
});
```

## view_cart

This event signifies that a user viewed their cart.

**Parameters (required and recommended)**

| Name       | Type                                      | Required | Example Value | Description                                                                                                                                                                                                                                                          |
| ---------- | ----------------------------------------- | -------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `value`    | `number`                                  | No       | 8.00          | <p>The monetary value of the event.<br>(*)<code>value</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p>                                                                         |
| `currency` | `string (ISO 4217)`                       | No       | EUR           | <p>Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.</p><p>(*) If you supply the <code>revenue</code> parameter, you must also supply the <code>currency</code> parameter so revenue metrics can be computed accurately.</p> |
| `items`    | [`Array<Item>`](events-reference.md#item) | **Yes**  |               | The items for the event.                                                                                                                                                                                                                                             |

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

## view_item

This event signifies that some content was shown to the user. Use this event to manage the most popular items viewed.

**Parameters (required and recommended)**

| Name       | Type                                      | Required  | Example Value | Description                                                                                                                                                                                    |
| ---------- | ----------------------------------------- | --------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `revenue`  | `number`                                  | **Yes**\* | 9.99          | <p>The monetary value of the event.<br>(*)<code>revenue</code> is typically required for meaningful reporting.</p><p>(*)<code>currency</code> is required if you set <code>revenue</code>.</p> |
| `currency` | `string (ISO 4217)`                       | **Yes\*** | EUR           | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.                                                                                                      |
| `items`    | [`Array<Item>`](events-reference.md#item) | **Yes**   |               | The items for the event.                                                                                                                                                                       |

## view_item_list

Log this event when the user has been presented with a list of items of a certain category.

#### Parameters <a href="parameters_35" id="parameters_35"></a>

| Name             | Type                                      | Required | Example value    | Description                                                       |
| ---------------- | ----------------------------------------- | -------- | ---------------- | ----------------------------------------------------------------- |
| `item_list_name` | `string`                                  | No       | Related products | The name of the list in which the item was presented to the user. |
| `items`          | [`Array<Item>`](events-reference.md#item) | **Yes**  |                  | The items for the event.                                          |

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

#### Parameters **(required and recommended)** <a href="parameters_27" id="parameters_27"></a>

| Name            | Type                                                                           | Required | Example Value | Description                                                                                                                                            |
| --------------- | ------------------------------------------------------------------------------ | -------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`            | `string`                                                                       | **Yes**  | SKU\_12345    | <p>The ID of an item.</p><p>If you don't have an item id, you can use the product id as value. This field is used as key for updates (ex : refund)</p> |
| `product`       | \<code>\</code>[`Object<Product>`](events-reference.md#product)\<code>\</code> | **Yes**  |               | The product details                                                                                                                                    |
| `variant`       | `string`                                                                       | No       | red           | The variant of the item.                                                                                                                               |
| `list_position` | `number`                                                                       | No       | 1             | The item's position in a list or collection.                                                                                                           |
| `discount`      | `number`                                                                       | No       | 2.00          | Monetary value of discount associated with a purchase                                                                                                  |
| `quantity`      | `number`                                                                       | **Yes**  | 2             | The quantity of the item.                                                                                                                              |
| `coupon`        | `string`                                                                       | No       | CHRISTMAS     | The coupon code associated with an item.                                                                                                               |
| `custom`        | `Object`                                                                       | No       |               | Object containing custom properties you want to send                                                                                                   |

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

#### Parameters **(required and recommended)** <a href="parameters_17" id="parameters_17"></a>

| Name                 | Type     | Required | Example Value  | Description                                                                                                                                         |
| -------------------- | -------- | -------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                 | `string` | **Yes**  | 845454         | User's id                                                                                                                                           |
| `email`              | `string` | Yes\*    | toto.domain.fr | <p>User's email<br>(*)<code>email</code> or is required if <code>id</code> is not set</p>                                                           |
| `consent_categories` | `Array`  | Yes\*    | \[1,3,4]       | <p>Consent categories of the user, to be allowed to share the event with partners.</p><p>(*) Automatically filled if you use Commanders Act CMP</p> |

## - ENUMERATED VALUE -

### Payment methods

Enumerated Values for payment methods :

| Property       | Value                       |
| -------------- | --------------------------- |
| payment_method | by_invoice                  |
| payment_method | by_bank_transfer_in_advance |
| payment_method | card                        |
| payment_method | check_in_advance            |
| payment_method | cod                         |
| payment_method | coupon                      |
| payment_method | direct_debit                |
| payment_method | online_payment_system       |
| payment_method | other                       |

### Purchase status

Enumerated Values for purchase status:

| Property | Value               |
| -------- | ------------------- |
| status   | canceled            |
| status   | delivered           |
| status   | in_progress         |
| status   | partially_delivered |
| status   | partially_returned  |
| status   | partially_shipped   |
| status   | pending_shipment    |
| status   | returned            |
| status   | shipped             |
| status   | pending             |
