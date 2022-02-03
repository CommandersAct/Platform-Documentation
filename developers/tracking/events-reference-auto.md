
## add\_payment\_info <a href="#add_payment_info" id="add_payment_info"></a>

This event signifies a user has submitted their payment information

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| payment_method | `string` | Yes | card | The chosen method of payment (see list of possible values below) |
| value | `string` | No | 22.53 | The monetary value of the event (shipping price and taxes included) after discount<br>(*) `value` is typically required for meaningful reporting |
| revenue | `string` | No | 16.00 | Revenue (shipping price and taxes excluded) after discount.<br>(*) `revenue` is typically required for meaningful reporting |
| coupon | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| items | <a href="#item">`Array<Object<Item>>`</a> | No | [{"product":{"id":1234}}] | The items for the event. |
| user | <a href="#user">`Object<User>`</a> | Yes | {"id":"84545"} | The items for the event. |

**Parameters (required and recommended)**

```javascript
cact('trigger', add_payment_info, {
  "payment_method": "card",
  "value": 22.53,
  "revenue": 16,
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

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| value | `string` | No | 22.53 | The monetary value of the event (shipping price and taxes included) after discount<br>(*) `value` is typically required for meaningful reporting |
| coupon | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| items | <a href="#item">`Array<Object<Item>>`</a> | Yes | [{"product":{"id":1234}}] | The items for the event. |
| user | <a href="#user">`Object<User>`</a> | Yes | {"id":"84545"} | The items for the event. |

**Parameters (required and recommended)**

```javascript
cact('trigger', add_shipping_info, {
  "value": 22.53,
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



## login <a href="#login" id="login"></a>

Send this event to signify that a user has logged in.

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| user | <a href="#user">`Object<User>`</a> | Yes | {"id":"84545"} | The items for the event. |
| method | `string` | No | LinkedIn | The method used to login. |

**Parameters (required and recommended)**

```javascript
cact('trigger', login, {
  "user": {
    "id": "84545"
  },
  "method": "LinkedIn"
})
```



## page\_view <a href="#page_view" id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| type | `string` | Yes | product_list | Page category. Equivalent to `tc_vars.env_template` |
| user | <a href="#user">`Object<User>`</a> | Yes | {"id":"84545"} | The items for the event. |

**Parameters (required and recommended)**

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

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| payment_method | `string` | Yes | card | Payment method type (see list of possible values below) |
| status | `string` | Yes | in_progress | Status of the conversion (see list of  below). Conversions with status "pending" are not included in default sum and counts aggregated on augmented user attributes feature |
| value | `string` | Yes | 22.53 | The monetary value of the event (shipping price and taxes included) after discount<br>(*) `value` is typically required for meaningful reporting |
| revenue | `string` | Yes | 16.00 | Revenue (shipping price and taxes excluded) after discount.<br>(*) `revenue` is typically required for meaningful reporting |
| shipping_amount | `string` | No | 3.33 | Shipping cost associated with a transaction. |
| tax_amount | `string` | No | 3.33 | Tax cost associated with a transaction. |
| coupon | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| type | `string` | Yes | offline | Type of conversion (online, offline, call etc.) |
| items | <a href="#item">`Array<Object<Item>>`</a> | Yes | [{"product":{"id":1234}}] | The items for the event. |
| user | <a href="#user">`Object<User>`</a> | Yes | {"id":"84545"} | The items for the event. |

**Parameters (required and recommended)**

```javascript
cact('trigger', purchase, {
  "payment_method": "card",
  "status": "in_progress",
  "value": 22.53,
  "revenue": 16,
  "shipping_amount": 3.33,
  "tax_amount": 3.33,
  "coupon": "CHRISTMAS",
  "type": "offline",
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



## add\_payment\_info <a href="#add_payment_info" id="add_payment_info"></a>

This event signifies a user has submitted their payment information

| Name | Type | Required | Example | Description |
| ---- | ---- | -------- | ------- | ----------- |
| payment_method | `string` | Yes | card | The chosen method of payment (see list of possible values below) |
| value | `string` | No | 22.53 | The monetary value of the event (shipping price and taxes included) after discount<br>(*) `value` is typically required for meaningful reporting |
| revenue | `string` | No | 16.00 | Revenue (shipping price and taxes excluded) after discount.<br>(*) `revenue` is typically required for meaningful reporting |
| coupon | `string` | No | CHRISTMAS | Coupon code used for a purchase. |
| items | <a href="#item">`Array<Object<Item>>`</a> | No | [{"product":{"id":1234}}] | The items for the event. |
| user | <a href="#user">`Object<User>`</a> | Yes | {"id":"84545"} | The items for the event. |

**Parameters (required and recommended)**

```javascript
cact('trigger', add_payment_info, {
  "payment_method": "card",
  "value": 22.53,
  "revenue": 16,
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


