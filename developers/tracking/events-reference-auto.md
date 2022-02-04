# Events reference



## add\_payment\_info <a href="#add_payment_info" id="add_payment_info"></a>

This event signifies a user has submitted their payment information

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `payment_method` | `string` | Yes | card | The chosen method of payment (see list of possible values below) |
| `revenue` | `number` | No* | 16.00 | Revenue (shipping price and taxes **excluded**) after discount.<br>(*) `revenue` is typically required for meaningful reporting |
| `value` | `number` | No* | 22.53 | The monetary value of the event (shipping price and taxes included) after discount<br>(*) `value` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `coupon` | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | No |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', add_payment_info, {
  "payment_method": "card",
  "revenue": 16,
  "value": 22.53,
  "currency": "EUR",
  "coupon": "CHRISTMAS",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## add\_shipping\_info <a href="#add_shipping_info" id="add_shipping_info"></a>

This event signifies a user has submitted their shipping information.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `value` | `number` | No* | 22.53 | The monetary value of the event (shipping price and taxes included) after discount<br>(*) `value` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `coupon` | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', add_shipping_info, {
  "value": 22.53,
  "currency": "EUR",
  "coupon": "CHRISTMAS",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## add\_to\_cart <a href="#add_to_cart" id="add_to_cart"></a>

This event signifies that an item was added to a cart for purchase.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `value` | `number` | Yes | 8.00 | The monetary value of the event |
| `currency` | `string` (ISO 4217) | Yes | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', add_to_cart, {
  "value": 8,
  "currency": "EUR",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## add\_to\_wishlist <a href="#add_to_wishlist" id="add_to_wishlist"></a>

The event signifies that an item was added to a wishlist. Use this event to identify popular gift items in your app.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `value` | `number` | No* | 8.00 | The monetary value of the event<br>(*) `value` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', add_to_wishlist, {
  "value": 8,
  "currency": "EUR",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## begin\_checkout <a href="#begin_checkout" id="begin_checkout"></a>

This event signifies that a user has begun a checkout.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `revenue` | `number` | No* | 16.00 | Revenue (shipping price and taxes **excluded**) after discount.<br>(*) `revenue` is typically required for meaningful reporting |
| `value` | `number` | Yes | 22.53 | The monetary value of the event (shipping price and taxes **included**) after discount |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `coupon` | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', begin_checkout, {
  "revenue": 16,
  "value": 22.53,
  "currency": "EUR",
  "coupon": "CHRISTMAS",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## generate\_lead <a href="#generate_lead" id="generate_lead"></a>

Log this event when a lead has been generated to understand the efficacy of your re-engagement campaigns.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `value` | `number` | No* | 8.00 | The monetary value of the event<br>(*) `value` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', generate_lead, {
  "value": 8,
  "currency": "EUR",
  "user": {
    "id": "84545"
  }
})
```



## login <a href="#login" id="login"></a>

Send this event to signify that a user has logged in.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `method` | `string` | No | LinkedIn | The method used to login. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', login, {
  "method": "LinkedIn",
  "user": {
    "id": "84545"
  }
})
```



## page\_view <a href="#page_view" id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `type` | `string` | Yes | product_list | Page category. Equivalent to `tc_vars.env_template` |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', page_view, {
  "type": "product_list",
  "user": {
    "id": "84545"
  }
})
```



## purchase <a href="#purchase" id="purchase"></a>

Fire this event when one or more items are purchased by a user.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `payment_method` | `string` | Yes | card | Payment method type (see list of possible values below) |
| `status` | `string` | Yes | in_progress | Status of the conversion (see list of  below). <br>Conversions with status "pending" are not included in default sum and counts aggregated on augmented user attributes feature |
| `revenue` | `number` | Yes | 16.00 | Revenue (shipping price and taxes **excluded**) after discount. |
| `shipping_amount` | `number` | No | 3.33 | Shipping cost associated with a transaction. |
| `tax_amount` | `number` | No | 3.20 | Tax cost associated with a transaction. |
| `value` | `number` | Yes | 22.53 | The monetary value of the event (shipping price and taxes **included**) after discount |
| `currency` | `string` (ISO 4217) | Yes | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format. |
| `coupon` | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| `type` | `string` | Yes | offline | Type of conversion (online, offline, call etc.) |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', purchase, {
  "payment_method": "card",
  "status": "in_progress",
  "revenue": 16,
  "shipping_amount": 3.33,
  "tax_amount": 3.2,
  "value": 22.53,
  "currency": "EUR",
  "coupon": "CHRISTMAS",
  "type": "offline",
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
    "id": "84545"
  }
})
```



## refund <a href="#refund" id="refund"></a>

Fire this event when a purchase was refund.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `revenue` | `number` | Yes | 16.00 | Revenue (shipping price and taxes **excluded**) after discount. |
| `shipping_amount` | `number` | No | 3.33 | Shipping cost associated with a transaction. |
| `tax_amount` | `number` | No | 3.20 | Tax cost associated with a transaction. |
| `value` | `number` | Yes | 22.53 | The monetary value of the event (shipping price and taxes **included**) after discount |
| `currency` | `string` (ISO 4217) | Yes | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format. |
| `coupon` | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| `type` | `string` | Yes | offline | Type of conversion (online, offline, call etc.) |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | No |   | `items` is required for partial refunds, but it can be omitted for full refunds. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', refund, {
  "revenue": 16,
  "shipping_amount": 3.33,
  "tax_amount": 3.2,
  "value": 22.53,
  "currency": "EUR",
  "coupon": "CHRISTMAS",
  "type": "offline",
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
    "id": "84545"
  }
})
```



## remove\_from\_cart <a href="#remove_from_cart" id="remove_from_cart"></a>

This event signifies that an item was removed from a cart.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `value` | `number` | No* | 8.00 | The monetary value of the event<br>(*) `value` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', remove_from_cart, {
  "value": 8,
  "currency": "EUR",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## search <a href="#search" id="search"></a>

Use this event to contextualize search operations. This event can help you identify the most popular content in your app.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `search_term` | `string` | Yes | t-shirt | The term that was searched for. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', search, {
  "search_term": "t-shirt",
  "user": {
    "id": "84545"
  }
})
```



## select\_content <a href="#select_content" id="select_content"></a>

This event signifies that a user has selected some content of a certain type. This event can help you identify popular content and categories of content in your app or click on internal promotion.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `content_type` | `string` | No | product | The type of selected content. |
| `item_id` | `string` | No | I_12345 | An identifier for the item that was selected. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', select_content, {
  "content_type": "product",
  "item_id": "I_12345",
  "user": {
    "id": "84545"
  }
})
```



## select\_item <a href="#select_item" id="select_item"></a>

This event signifies an item was selected from a list.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', select_item, {
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## sign\_up <a href="#sign_up" id="sign_up"></a>

This event indicates that a user has signed up for an account.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `method` | `string` | No | email | The method used for sign up. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', sign_up, {
  "method": "email",
  "user": {
    "id": "84545"
  }
})
```



## view\_cart <a href="#view_cart" id="view_cart"></a>

This event signifies that a user viewed their cart.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `value` | `number` | No* | 8.00 | The monetary value of the event<br>(*) `value` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', view_cart, {
  "value": 8,
  "currency": "EUR",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## view\_item <a href="#view_item" id="view_item"></a>

This event signifies that some content was shown to the user. Use this event to manage the most popular items viewed.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `revenue` | `number` | No* | 16.00 | Revenue (shipping price and taxes **excluded**) after discount.<br>(*) `revenue` is typically required for meaningful reporting |
| `currency` | `string` (ISO 4217) | No* | EUR | Currency of the purchase or items associated with the event, in 3-letter ISO 4217 format.<br>(*) If you supply a pricing parameter (e.g. `value`, `revenue`), the currency becomes mandatory. |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', view_item, {
  "revenue": 16,
  "currency": "EUR",
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```



## view\_item\_list <a href="#view_item_list" id="view_item_list"></a>

Log this event when the user has been presented with a list of items of a certain category.

**Parameters (required and recommended)**

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| `items` | <a href="#item">`Array<Object<Item>>`</a> | Yes |   | The items for the event. |
| `user` | <a href="#user">`Object<User>`</a> | Yes |   | Object containing user identity (`id`, `email`, ...) and consents (`consent_categories`). |

**Example**

```javascript
cact('trigger', view_item_list, {
  "items": [
    {
      "product": {
        "id": 1234
      }
    }
  ],
  "user": {
    "id": "84545"
  }
})
```




## - COMMON SCHEMAS -

...todo user/item/product...

## - ENUMERATED VALUE -

...todo payment_method/purchase#status...

## Pricing rules

1. currency required when any pricing information specified
2. calculation value = fn(revenue, ship, tax, discount)

Examples:

...


