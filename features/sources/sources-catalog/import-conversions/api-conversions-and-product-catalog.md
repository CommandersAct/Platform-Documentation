# API Conversions and Product catalog

## Commanders Act Data API v2.0.0 <a href="#commanders-act-data-api" id="commanders-act-data-api"></a>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

It is highly recommended that you send multiple objects in one HTTP request. This API allows streaming using newline separated JSON format or ndjson ([http://ndjson.org/](http://ndjson.org/))

### Rate-limits <a href="#rate-limits" id="rate-limits"></a>

* You may send up to 30 requests per second
* You may have up to 30 concurrent connections
* If you send many conversions/products/etc. in bulk, the upload speed will be limited to 30 conversions/products/etc. per second

#### Rate limiting examples <a href="#rate-limiting-examples" id="rate-limiting-examples"></a>

* If you send 1 conversion per request you will be limited to 30 requests per second
* If you send 90 conversions in one request your upload will be completed in about 3 seconds
* If you send 40 requests, each with one conversion in the same second, 30 of them will be processed and 10 of them will be rejected
* If you send 3 requests, each with 100 conversions they will be completed in 10 seconds

### Limitations

* You can send up to 150 conversion items

### Date formats <a href="#date-formats" id="date-formats"></a>

Use the long format with timezone for passing ISO-8601 dates. The following formats are accepted:

* "2019-04-29T13:47:47.315Z"
* "2019-04-29T13:47:47Z"
* "2019-04-29T13:47:47.315+02:00"
* "2019-04-29T13:47:47+02:00"

### Errors <a href="#errors" id="errors"></a>

Errors are always returned as an array of objects in the top-level "errors" property.

#### Errors in bulk operations <a href="#errors-in-bulk-operations" id="errors-in-bulk-operations"></a>

For bulk operations you may have "errors" and "data" properties at the same time since some objects may have errors while others may not. Bulk errors are aggregated which means there won't be an error for each instance of an error but one error for each type of error with the number of occurrences and some examples of line numbers or ids.

```
{
  "errors": [
    {
      "code": "YOU_CAN_CHECK_THIS_IN_CODE",
      "detail": "This explains the error",
      "meta": {
        "context_property_example": "value_example",
        "error_count": 3,
        "line_numbers": [34, 45],
        "ids": [
          "c9017b85-8016-4f13-88b4-18d57c67b866",
          "12e0c3cb-7e8d-462f-9232-f7c61a900738"
        ]
      }
    }
  ]
  "data": {
    "accepted_object_count": 4,
    "rejected_object_count": 3
  }
}
```

#### Error object <a href="#error-object" id="error-object"></a>

Error objects have the following properties

| Property | Type   | Required | Description                                                                                                                              |
| -------- | ------ | -------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| code     | string | true     | Always present and contains error code that can be checked programmatically                                                              |
| detail   | string | true     | Human readable message that explains the problem. You should not check the value of this property programmatically because it may change |
| meta     | object | false    | Error specific object that contains details about what generated the error                                                               |

Base URLs:

* [https://api.commander1.com/v2/{siteId}](https://api.commander1.com/v2/%7BsiteId%7D)

## Authentication <a href="#authentication" id="authentication"></a>

* HTTP Authentication, scheme: bearer Token will be provided by our support/consulting team

## Default <a href="#commanders-act-data-api-default" id="commanders-act-data-api-default"></a>

### Upsert conversions <a href="#upsert-conversions" id="upsert-conversions"></a>

> Code samples

```
POST https://api.commander1.com/v2/{siteId}/conversions/bulk HTTP/1.1
Host: api.commander1.com
Content-Type: application/x-ndjson
Accept: application/json
Authorization: Bearer NJtcKaoCYu...mGZDxRgMBMUw==
```

`POST /conversions/bulk`

This endpoint creates and updates conversions. Your request will be processed asynchronously. It can take up to 1 hour until the request is processed and updates are made in the database.

> Body parameter

```
{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","user":{"user_email":"user@example.com"},"type":"offline","status":"in_progress","created":"2018-01-01T20:00:00.000+01:00","updated":"2018-01-01T20:00:00.000+01:00","acknowledged":true,"currency":"EUR","comment":"Package needs to be smaller than 30cm by 30cm","billing_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"contact_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"shipping_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"shipping_provider":"UPS","shipping_tracking_code":"702c7a16-2c3d-4946-bb35-69ba540773f6","payment_method":"card","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"shipping_amount":0,"discount_amount":0,"tax_amount":5,"final_amount":10,"custom":{"internal_reference":"fa34dc2","referer":"user@example.com","website_version":"2.4"},"conversion_items":[{"id":"68cd1310-4b7a-454c-99fb-2510f0e156ec","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"final_amount":10,"price":10,"original_item":true,"custom":{"remarketing_campaign":"christmas_2018","time_to_checkout":"25 minutes","ab_testing_group":"3245fcda"},"product":{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}},{"id":"68cd1310-4b7a-454c-99fb-2510f0e156ec","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"final_amount":10,"price":10,"original_item":true,"custom":{"remarketing_campaign":"christmas_2018","time_to_checkout":"25 minutes","ab_testing_group":"3245fcda"},"product":{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}}]}
{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","user":{"user_email":"user@example.com"},"type":"offline","status":"in_progress","created":"2018-01-01T20:00:00.000+01:00","updated":"2018-01-01T20:00:00.000+01:00","acknowledged":true,"currency":"EUR","comment":"Package needs to be smaller than 30cm by 30cm","billing_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"contact_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"shipping_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"shipping_provider":"UPS","shipping_tracking_code":"702c7a16-2c3d-4946-bb35-69ba540773f6","payment_method":"card","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"shipping_amount":0,"discount_amount":0,"tax_amount":5,"final_amount":10,"custom":{"internal_reference":"fa34dc2","referer":"user@example.com","website_version":"2.4"},"conversion_items":[{"id":"68cd1310-4b7a-454c-99fb-2510f0e156ec","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"final_amount":10,"price":10,"original_item":true,"custom":{"remarketing_campaign":"christmas_2018","time_to_checkout":"25 minutes","ab_testing_group":"3245fcda"},"product":{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}},{"id":"68cd1310-4b7a-454c-99fb-2510f0e156ec","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"final_amount":10,"price":10,"original_item":true,"custom":{"remarketing_campaign":"christmas_2018","time_to_checkout":"25 minutes","ab_testing_group":"3245fcda"},"product":{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}}]}
{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","user":{"user_email":"user@example.com"},"type":"offline","status":"in_progress","created":"2018-01-01T20:00:00.000+01:00","updated":"2018-01-01T20:00:00.000+01:00","acknowledged":true,"currency":"EUR","comment":"Package needs to be smaller than 30cm by 30cm","billing_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"contact_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"shipping_address":{"country":"France","iso_country_code":"FR","country_code":"FRA","region":"Ile-de-France","locality":"Paris","postal_code":"75009","recipient":"Commanders Act","street_address":"3-5 Rue Saint-Georges","full_address":null,"label":"home","coordinates":{"latitude":48.857764,"longitude":2.33935}},"shipping_provider":"UPS","shipping_tracking_code":"702c7a16-2c3d-4946-bb35-69ba540773f6","payment_method":"card","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"shipping_amount":0,"discount_amount":0,"tax_amount":5,"final_amount":10,"custom":{"internal_reference":"fa34dc2","referer":"user@example.com","website_version":"2.4"},"conversion_items":[{"id":"68cd1310-4b7a-454c-99fb-2510f0e156ec","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"final_amount":10,"price":10,"original_item":true,"custom":{"remarketing_campaign":"christmas_2018","time_to_checkout":"25 minutes","ab_testing_group":"3245fcda"},"product":{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}},{"id":"68cd1310-4b7a-454c-99fb-2510f0e156ec","original_quantity":3,"cancelled_quantity":1,"returned_quantity":1,"exchanged_quantity":0,"final_quantity":1,"original_amount":30,"cancelled_amount":10,"returned_amount":10,"exchanged_amount":0,"final_amount":10,"price":10,"original_item":true,"custom":{"remarketing_campaign":"christmas_2018","time_to_checkout":"25 minutes","ab_testing_group":"3245fcda"},"product":{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}}]}
```

#### Parameters <a href="#upsert-conversions-parameters" id="upsert-conversions-parameters"></a>

| Name          | In     | Type    | Required | Description                                                                 |
| ------------- | ------ | ------- | -------- | --------------------------------------------------------------------------- |
| Authorization | header | string  | true     | Authorization token                                                        |
| overwrite     | query  | boolean | false    | Determines if conversions should be fully replaced (`true`) or partially updated (`false` - default). |
| body          | body   | [Conversion](api-conversions-and-product-catalog.md#tocs\_conversion) | true     | Conversions as newline delimited JSON strings                              |

### Overwrite Parameter Behavior  

The `overwrite` url parameter determines how conversions are processed when an existing `id` is found:

- **`false`** *(default)*:  
   - Only the specified fields will be updated.  
   - Unspecified fields will retain their existing values.

- **`true`**:  
   - The existing conversion will be **fully replaced** with the new data provided.  
   - Unspecified fields will be reset to their default or empty values.  

If you need to replace a conversion entirely, set `overwrite=true`.


> Example responses

> 202 Response

```
{
  "data": {
    "accepted_object_count": 4,
    "rejected_object_count": 0
  }
}
```

> 400 Cannot parse nd-json line

```
{
  "errors": [
    {
      "code": "PARSE_ERROR",
      "detail": "Cannot parse nd-json"
    }
  ],
  "data": {}
}
```

> 400 Missing required property

```
{
  "errors": [
    {
      "code": "MISSING_REQUIRED_PROPERTY",
      "detail": "should have required property 'id'\n",
      "meta": {
        "line_numbers": [
          34,
          45
        ],
        "error_count": 2,
        "ids": [
          "c9017b85-8016-4f13-88b4-18d57c67b866",
          "12e0c3cb-7e8d-462f-9232-f7c61a900738"
        ]
      }
    }
  ],
  "data": {
    "accepted_object_count": 4,
    "rejected_object_count": 2
  }
}
```

> 400 Invalid property type

```
{
  "errors": [
    {
      "code": "INVALID_PROPERTY_TYPE",
      "detail": "\"original_amount\" property is not a number",
      "meta": {
        "property": "original_amount",
        "line_numbers": [
          34,
          45
        ],
        "error_count": 2,
        "ids": [
          "c9017b85-8016-4f13-88b4-18d57c67b866",
          "12e0c3cb-7e8d-462f-9232-f7c61a900738"
        ]
      }
    }
  ],
  "data": {
    "accepted_object_count": 4,
    "rejected_object_count": 2
  }
}
```

> 400 Invalid property format

```
{
  "errors": [
    {
      "code": "INVALID_PROPERTY_FORMAT",
      "detail": "\"original_amount\" property is not a number",
      "meta": {
        "property": "original_amount",
        "line_numbers": [
          34,
          45
        ],
        "error_count": 2,
        "ids": [
          "c9017b85-8016-4f13-88b4-18d57c67b866",
          "12e0c3cb-7e8d-462f-9232-f7c61a900738"
        ]
      }
    }
  ],
  "data": {
    "accepted_object_count": 4,
    "rejected_object_count": 2
  }
}
```

> 401 Authorization header is missing

```
{
  "errors": [
    {
      "code": "MISSING_AUTHORIZATION_HEADER",
      "detail": "The \"Authorization\" header is required"
    }
  ]
}
```

> 401 Token type is missing

```
{
  "errors": [
    {
      "code": "UNKNOWN_TOKEN_TYPE",
      "detail": "The token type is missing"
    }
  ]
}
```

> 401 The token type is invalid

```
{
  "errors": [
    {
      "code": "INVALID_TOKEN_TYPE",
      "detail": "The token type \"Bear\" is invalid. Expecting \"Bearer\" instead"
    }
  ]
}
```

> 401 The provided token is unknown

```
{
  "errors": [
    {
      "code": "UNKNOWN_TOKEN",
      "detail": "The provided token is unknown. Please contact our support team support@commandersact.com"
    }
  ]
}
```

> 403 Response

```
{
  "errors": [
    {
      "code": "SITE_ACCESS_FORBIDDEN",
      "detail": "You cannot access this site"
    }
  ]
}
```

> Too Many Requests

```
{
  "description": "You have too many open connections",
  "errors": [
    {
      "code": "CONNECTION_LIMIT_REACHED",
      "detail": "Your account is limited to 30 simultaneous connections"
    }
  ]
}
```

```
{
  "description": "You have reached the request limit",
  "errors": [
    {
      "code": "REQUEST_LIMIT_REACHED",
      "detail": "Your account is limited to 30 requests per second"
    }
  ]
}
```

> 500 Response

```
{
  "errors": [
    {
      "code": "SERVER_ERROR",
      "detail": "An internal error occurred. Please contact our support team support@commandersact.com"
    }
  ]
}
```

#### Responses <a href="#upsert-conversions-responses" id="upsert-conversions-responses"></a>

| Status | Meaning                                                                    | Description                                                       | Schema |
| ------ | -------------------------------------------------------------------------- | ----------------------------------------------------------------- | ------ |
| 202    | [Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)              | All objects are accepted for processing                           | None   |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Cannot process request or part of the request due to client error | None   |
| 401    | [Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)            | Cannot identify the API caller                                    | None   |
| 403    | [Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)             | API caller does not have access to this resource                  | None   |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too Many Requests                                                 | None   |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal server error                                             | None   |

#### Response Schema <a href="#upsert-conversions-responseschema" id="upsert-conversions-responseschema"></a>

### Upsert products <a href="#upsert-products" id="upsert-products"></a>

> Code samples

```
POST https://api.commander1.com/v2/{siteId}/products/bulk HTTP/1.1
Host: api.commander1.com
Content-Type: application/x-ndjson

Authorization: Bearer NJtcKaoCYu...mGZDxRgMBMUw==
```

`POST /products/bulk`

This endpoint creates and updates products. Your request will be processed asynchronously. It can take up to 24 hours until the request is processed and updates are made in the database.

> Body parameter

```
{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}
{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}
{"id":"db050bb1-810d-4420-a6fb-c1ce472a4ca9","name":"Mug Commanders Act","description":"White stoneware mug with C-Handle is the perfect cup for any beverage","category_1":"Home","category_2":"Kitchen","category_3":"Accessories","category_4":"Containers","category_5":"Mugs","tags":["mugs","handle","white","brand"],"condition":"new","availability":"in_stock","availability_date":"2019-02-06T17:41:31.427+01:00","expiration_date":"2019-02-06T17:41:31.427+01:00","price":10,"sale_price":8,"currency":"EUR","image_link":"https://commandersact.com/images/shopping/mug_hi_res.jpg","link":"https://commandersact.com/shopping/mug","brand":"Commanders Act","width":6.4,"length":7.3,"height":9.5,"weight":80.7,"size":"medium","colors":["white","red"],"gtin":"134588842456789000","mpn":"134588842","custom":{"internal_category_id":721,"warehouse":"building B","box_barcode":1830135586179}}
```

#### Parameters <a href="#upsert-products-parameters" id="upsert-products-parameters"></a>

| Name          | In     | Type                                                            | Required | Description                                |
| ------------- | ------ | --------------------------------------------------------------- | -------- | ------------------------------------------ |
| Authorization | header | string                                                          | true     | Authorization token                        |
| body          | body   | [Product](api-conversions-and-product-catalog.md#tocs\_product) | true     | Products as newline delimited JSON strings |

#### Responses <a href="#upsert-products-responses" id="upsert-products-responses"></a>

| Status | Meaning                                                                 | Description   | Schema |
| ------ | ----------------------------------------------------------------------- | ------------- | ------ |
| 202    | [Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)           | Accepted      | None   |
| 207    | [Multi-Status](https://tools.ietf.org/html/rfc2518#section-10.2)        | Multi-Status  | None   |
| 401    | [Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)         | Unauthorized  | None   |
| 405    | [Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5) | Invalid input | None   |

## Schemas <a href="#schemas" id="schemas"></a>

### Conversion <a href="#tocs_conversion" id="tocs_conversion"></a>

```
{
  "id": "db050bb1-810d-4420-a6fb-c1ce472a4ca9",
  "user": {
    "email": "user@example.com", 
    "consent_categories": [1,3]
  },
  "type": "offline",
  "status": "in_progress",
  "created": "2018-01-01T20:00:00.000+01:00",
  "updated": "2018-01-01T20:00:00.000+01:00",
  "acknowledged": true,
  "currency": "EUR",
  "comment": "Package needs to be smaller than 30cm by 30cm",
  "billing_address": {
    "country": "France",
    "iso_country_code": "FR",
    "country_code": "FRA",
    "region": "Ile-de-France",
    "locality": "Paris",
    "postal_code": "75009",
    "recipient": "Commanders Act",
    "street_address": "3-5 Rue Saint-Georges",
    "full_address": null,
    "label": "home",
    "coordinates": {
      "latitude": 48.857764,
      "longitude": 2.33935
    }
  },
  "contact_address": {
    "country": "France",
    "iso_country_code": "FR",
    "country_code": "FRA",
    "region": "Ile-de-France",
    "locality": "Paris",
    "postal_code": "75009",
    "recipient": "Commanders Act",
    "street_address": "3-5 Rue Saint-Georges",
    "full_address": null,
    "label": "home",
    "coordinates": {
      "latitude": 48.857764,
      "longitude": 2.33935
    }
  },
  "shipping_address": {
    "country": "France",
    "iso_country_code": "FR",
    "country_code": "FRA",
    "region": "Ile-de-France",
    "locality": "Paris",
    "postal_code": "75009",
    "recipient": "Commanders Act",
    "street_address": "3-5 Rue Saint-Georges",
    "full_address": null,
    "label": "home",
    "coordinates": {
      "latitude": 48.857764,
      "longitude": 2.33935
    }
  },
  "shipping_provider": "UPS",
  "shipping_tracking_code": "702c7a16-2c3d-4946-bb35-69ba540773f6",
  "payment_method": "card",
  "original_quantity": 3,
  "cancelled_quantity": 1,
  "returned_quantity": 1,
  "exchanged_quantity": 0,
  "final_quantity": 1,
  "original_amount": 30,
  "cancelled_amount": 10,
  "returned_amount": 10,
  "exchanged_amount": 0,
  "shipping_amount": 0,
  "discount_amount": 0,
  "tax_amount": 5,
  "final_amount": 10,
  "custom": {
    "internal_reference": "fa34dc2",
    "referer": "user@example.com",
    "website_version": "2.4"
  },
  "conversion_items": [
    {
      "id": "68cd1310-4b7a-454c-99fb-2510f0e156ec",
      "original_quantity": 3,
      "cancelled_quantity": 1,
      "returned_quantity": 1,
      "exchanged_quantity": 0,
      "final_quantity": 1,
      "original_amount": 30,
      "cancelled_amount": 10,
      "returned_amount": 10,
      "exchanged_amount": 0,
      "final_amount": 10,
      "price": 10,
      "original_item": true,
      "custom": {
        "remarketing_campaign": "christmas_2018",
        "time_to_checkout": "25 minutes",
        "ab_testing_group": "3245fcda"
      },
      "product": {
        "id": "db050bb1-810d-4420-a6fb-c1ce472a4ca9",
        "name": "Mug Commanders Act",
        "description": "White stoneware mug with C-Handle is the perfect cup for any beverage",
        "category_1": "Home",
        "category_2": "Kitchen",
        "category_3": "Accessories",
        "category_4": "Containers",
        "category_5": "Mugs",
        "tags": [
          "mugs",
          "handle",
          "white",
          "brand"
        ],
        "condition": "new",
        "availability": "in_stock",
        "availability_date": "2019-02-06T17:41:31.427+01:00",
        "expiration_date": "2019-02-06T17:41:31.427+01:00",
        "price": 10,
        "sale_price": 8,
        "currency": "EUR",
        "image_link": "https://commandersact.com/images/shopping/mug_hi_res.jpg",
        "link": "https://commandersact.com/shopping/mug",
        "brand": "Commanders Act",
        "width": 6.4,
        "length": 7.3,
        "height": 9.5,
        "weight": 80.7,
        "size": "medium",
        "colors": [
          "white",
          "red"
        ],
        "gtin": "134588842456789000",
        "mpn": "134588842",
        "custom": {
          "internal_category_id": 721,
          "warehouse": "building B",
          "box_barcode": 1830135586179
        }
      }
    },
    {
      "id": "68cd1310-4b7a-454c-99fb-2510f0e156ec",
      "original_quantity": 3,
      "cancelled_quantity": 1,
      "returned_quantity": 1,
      "exchanged_quantity": 0,
      "final_quantity": 1,
      "original_amount": 30,
      "cancelled_amount": 10,
      "returned_amount": 10,
      "exchanged_amount": 0,
      "final_amount": 10,
      "price": 10,
      "original_item": true,
      "custom": {
        "remarketing_campaign": "christmas_2018",
        "time_to_checkout": "25 minutes",
        "ab_testing_group": "3245fcda"
      },
      "product": {
        "id": "db050bb1-810d-4420-a6fb-c1ce472a4ca9",
        "name": "Mug Commanders Act",
        "description": "White stoneware mug with C-Handle is the perfect cup for any beverage",
        "category_1": "Home",
        "category_2": "Kitchen",
        "category_3": "Accessories",
        "category_4": "Containers",
        "category_5": "Mugs",
        "tags": [
          "mugs",
          "handle",
          "white",
          "brand"
        ],
        "condition": "new",
        "availability": "in_stock",
        "availability_date": "2019-02-06T17:41:31.427+01:00",
        "expiration_date": "2019-02-06T17:41:31.427+01:00",
        "price": 10,
        "sale_price": 8,
        "currency": "EUR",
        "image_link": "https://commandersact.com/images/shopping/mug_hi_res.jpg",
        "link": "https://commandersact.com/shopping/mug",
        "brand": "Commanders Act",
        "width": 6.4,
        "length": 7.3,
        "height": 9.5,
        "weight": 80.7,
        "size": "medium",
        "colors": [
          "white",
          "red"
        ],
        "gtin": "134588842456789000",
        "mpn": "134588842",
        "custom": {
          "internal_category_id": 721,
          "warehouse": "building B",
          "box_barcode": 1830135586179
        }
      }
    }
  ]
}
```

It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions

#### Properties <a href="#properties" id="properties"></a>

| Name                      | Type                                                                             | Required | Restrictions | Description                                                                                                                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------- | -------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                        | string(1-50)                                                                     | true     | none         | Conversion id. Used as key for updates                                                                                                                                                                                                             |
| user                      | object                                                                           | true     | none         | All properties that you add here will be used as conditions for matching users in our database. You must ensure that values used inside these properties are unique. Use same property names as those defined in variables interface for the user. |
| » user.email              | string(1-250)                                                                    | false    | none         | Email of the user                                                                                                                                                                                                                                  |
| »user.consent\_categories | string                                                                           | false    | none         | Consent categories of the user, to be allowed to share conversions with partners                                                                                                                                                                   |
| type                      | string(1-250)                                                                    | true     | none         | Type of conversion (online, offline, call etc.)                                                                                                                                                                                                    |
| status                    | string                                                                           | true     | none         | Status of your conversion (see list of possible values below). Conversions with status "pending" are not included in default sum and counts aggregated on a user.                                                                                  |
| created                   | string(ISO-8601)                                                                 | true     | none         | Time when conversion occurred. See "Date formats" section above for a list of allowed formats.                                                                                                                                                     |
| updated                   | string(ISO-8601)                                                                 | false    | none         | Time when conversion was updated. See "Date formats" section above for a list of allowed formats.                                                                                                                                                  |
| acknowledged              | boolean                                                                          | false    | none         | Set to true if conversion was acknowledged                                                                                                                                                                                                         |
| currency                  | string(ISO-4217)                                                                 | true     | none         | Currency                                                                                                                                                                                                                                           |
| comment                   | string(1-250)                                                                    | false    | none         | Comment of the buyer                                                                                                                                                                                                                               |
| billing\_address          | [Address](api-conversions-and-product-catalog.md#tocs\_address)                  | false    | none         | It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions                                                                                                                             |
| contact\_address          | [Address](api-conversions-and-product-catalog.md#tocs\_address)                  | false    | none         | It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions                                                                                                                             |
| shipping\_address         | [Address](api-conversions-and-product-catalog.md#tocs\_address)                  | false    | none         | It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions                                                                                                                             |
| shipping\_provider        | string(1-250)                                                                    | false    | none         | Shipping provider                                                                                                                                                                                                                                  |
| shipping\_tracking\_code  | string(1-250)                                                                    | false    | none         | Shipping tracking code                                                                                                                                                                                                                             |
| payment\_method           | string                                                                           | false    | none         | Payment method type (see list of possible values below)                                                                                                                                                                                            |
| payment\_provider         | string                                                                           | false    | none         | Payment provider used for this transaction                                                                                                                                                                                                         |
| original\_quantity        | float                                                                            | false    | read-only    | Sum of all articles in the original conversion (CALCULATED)                                                                                                                                                                                        |
| cancelled\_quantity       | float                                                                            | false    | read-only    | Quantity of cancelled articles in the conversion (CALCULATED)                                                                                                                                                                                      |
| returned\_quantity        | float                                                                            | false    | read-only    | Quantity of returned articles in the conversion (CALCULATED)                                                                                                                                                                                       |
| exchanged\_quantity       | float                                                                            | false    | read-only    | Quantity of exchanged articles in the conversion (CALCULATED)                                                                                                                                                                                      |
| final\_quantity           | float                                                                            | false    | read-only    | Quantity of articles in final transaction for this conversion (original\_quantity - cancelled\_quantity - returned\_quantity - exchanged\_quantity) (CALCULATED)                                                                                   |
| original\_amount          | float                                                                            | false    | write-once   | Original amount for this conversion (shipping price and taxes included)                                                                                                                                                                            |
| cancelled\_amount         | float                                                                            | false    | none         | Cancelled amount for this conversion                                                                                                                                                                                                               |
| returned\_amount          | float                                                                            | false    | none         | Returned amount for this conversion                                                                                                                                                                                                                |
| exchanged\_amount         | float                                                                            | false    | none         | Exchanged amount for this conversion                                                                                                                                                                                                               |
| shipping\_amount          | float                                                                            | false    | none         | Shipping amount for this conversion                                                                                                                                                                                                                |
| discount\_amount          | float                                                                            | false    | none         | Discount amount for this conversion                                                                                                                                                                                                                |
| tax\_amount               | float                                                                            | false    | none         | Tax amount for this conversion                                                                                                                                                                                                                     |
| final\_amount             | float                                                                            | false    | none         | Final amount for this conversion after returns, exchanges, cancellations etc. (shipping price and taxes included). This represents the overall transaction amount between the buyer and the seller                                                 |
| custom                    | object                                                                           | false    | none         | Object containing custom properties                                                                                                                                                                                                                |
| conversion\_items         | \[[ConversionItem](api-conversions-and-product-catalog.md#tocs\_conversionitem)] | true     | none         | List of products in the conversion + their own attributes. You cannot have the same product twice inside a conversion unless you provide a conversion item id                                                                                      |

**Enumerated Values**

| Property        | Value                           |
| --------------- | ------------------------------- |
| status          | canceled                        |
| status          | delivered                       |
| status          | in\_progress                    |
| status          | partially\_delivered            |
| status          | partially\_returned             |
| status          | partially\_shipped              |
| status          | pending\_shipment               |
| status          | returned                        |
| status          | shipped                         |
| status          | pending                         |
| payment\_method | by\_bank\_transfer\_in\_advance |
| payment\_method | by\_invoice                     |
| payment\_method | card                            |
| payment\_method | check\_in\_advance              |
| payment\_method | cod                             |
| payment\_method | coupon                          |
| payment\_method | direct\_debit                   |
| payment\_method | online\_payment\_system         |
| payment\_method | other                           |

### ConversionItem <a href="#tocs_conversionitem" id="tocs_conversionitem"></a>

```
{
  "id": "68cd1310-4b7a-454c-99fb-2510f0e156ec",
  "original_quantity": 3,
  "cancelled_quantity": 1,
  "returned_quantity": 1,
  "exchanged_quantity": 0,
  "final_quantity": 1,
  "original_amount": 30,
  "cancelled_amount": 10,
  "returned_amount": 10,
  "exchanged_amount": 0,
  "final_amount": 10,
  "price": 10,
  "original_item": true,
  "custom": {
    "remarketing_campaign": "christmas_2018",
    "time_to_checkout": "25 minutes",
    "ab_testing_group": "3245fcda"
  },
  "product": {
    "id": "db050bb1-810d-4420-a6fb-c1ce472a4ca9",
    "name": "Mug Commanders Act",
    "description": "White stoneware mug with C-Handle is the perfect cup for any beverage",
    "category_1": "Home",
    "category_2": "Kitchen",
    "category_3": "Accessories",
    "category_4": "Containers",
    "category_5": "Mugs",
    "tags": [
      "mugs",
      "handle",
      "white",
      "brand"
    ],
    "condition": "new",
    "availability": "in_stock",
    "availability_date": "2019-02-06T17:41:31.427+01:00",
    "expiration_date": "2019-02-06T17:41:31.427+01:00",
    "price": 10,
    "sale_price": 8,
    "currency": "EUR",
    "image_link": "https://commandersact.com/images/shopping/mug_hi_res.jpg",
    "link": "https://commandersact.com/shopping/mug",
    "brand": "Commanders Act",
    "width": 6.4,
    "length": 7.3,
    "height": 9.5,
    "weight": 80.7,
    "size": "medium",
    "colors": [
      "white",
      "red"
    ],
    "gtin": "134588842456789000",
    "mpn": "134588842",
    "custom": {
      "internal_category_id": 721,
      "warehouse": "building B",
      "box_barcode": 1830135586179
    }
  }
}
```

It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions

#### Properties <a href="#properties" id="properties"></a>

| Name                | Type                                                            | Required | Restrictions | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------- | --------------------------------------------------------------- | -------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                  | string                                                          | true     | none         | Id of this item in the conversion. This id is required. If you don't have an item id in your database and the same product id cannot repeat within a conversion you can use the product id as value. This field is used for identifying the item in updates.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| original\_quantity  | float                                                           | true     | none         | Quantity of items in the original conversion                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| cancelled\_quantity | float                                                           | false    | none         | Quantity of cancelled items                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| returned\_quantity  | float                                                           | false    | none         | Quantity of returned items                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| exchanged\_quantity | float                                                           | false    | none         | Quantity of exchanged items                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| final\_quantity     | float                                                           | false    | none         | Quantity of items in final transaction (original\_quantity - cancelled\_quantity - returned\_quantity - exchanged\_quantity)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| original\_amount    | float                                                           | false    | none         | Original amount for this item                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| cancelled\_amount   | float                                                           | false    | none         | Cancelled amount for this item                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| returned\_amount    | float                                                           | false    | none         | Returned amount for this item                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| exchanged\_amount   | float                                                           | false    | none         | Exchanged amount for this item                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| final\_amount       | float                                                           | false    | none         | Final amount for this item (original\_amount - cancelled\_amount - returned\_amount - exchanged\_amount)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| price               | float                                                           | false    | none         | Price of item (using same currency as for conversion)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| original\_item      | boolean                                                         | false    | none         | Wether this item was present in the original conversion. This is automatically set to false to all items added in conversion updates                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| custom              | object                                                          | false    | none         | Object containing custom properties                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| product             | [Product](api-conversions-and-product-catalog.md#tocs\_product) | true     | none         | <p>There are three ways to have product information in your conversion items. First method is to put product properties inline for each conversion item. Second method is to synchronize your product catalog with our database using "POST /products/bulk" endpoint and only send product ids in conversion items (our server will copy product properties from catalog). Third method is a combination of previous ones and implies having a product catalog and send the product information inline. In case a property is present in both catalog product and inline product, properties from inline product will overwrite properties from catalog. This method is useful when product information is incomplete or complementary in inline products.<br>It is recommended to send products inline, except when you do not have all product information. In most cases you don't need to use the catalog. It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions.<br>When you only send the id of the product in a conversion item, you need to make sure that your catalog already contains the product, otherwise product properties will not be added to your conversion item.</p> |

### Address <a href="#tocs_address" id="tocs_address"></a>

```
{
  "country": "France",
  "iso_country_code": "FR",
  "country_code": "FRA",
  "region": "Ile-de-France",
  "locality": "Paris",
  "postal_code": "75009",
  "recipient": "Commanders Act",
  "street_address": "3-5 Rue Saint-Georges",
  "full_address": null,
  "label": "home",
  "coordinates": {
    "latitude": 48.857764,
    "longitude": 2.33935
  }
}
```

It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions

#### Properties <a href="#properties" id="properties"></a>

| Name               | Type             | Required | Restrictions | Description                                                                                              |
| ------------------ | ---------------- | -------- | ------------ | -------------------------------------------------------------------------------------------------------- |
| country            | string(1-250)    | false    | none         | Readable country name                                                                                    |
| iso\_country\_code | string(ISO-3166) | false    | none         | ISO-3166 country code                                                                                    |
| country\_code      | string           | false    | none         | Use this field in case you use country codes other than ISO-3166                                         |
| region             | string(1-250)    | false    | none         | Administrative region                                                                                    |
| locality           | string(1-250)    | false    | none         | Name of city/town/village etc.                                                                           |
| postal\_code       | string(1-250)    | false    | none         | Postal code                                                                                              |
| recipient          | string(1-250)    | false    | none         | Recipient name                                                                                           |
| street\_address    | string(1-250)    | false    | none         | Street name, street number, building number etc.                                                         |
| full\_address      | string(1-250)    | false    | none         | Full address as a string that can contain newlines. Not usable in segmentation but available for exports |
| label              | string(1-250)    | false    | none         | Label for this address (home, work etc.)                                                                 |
| coordinates        | object           | false    | none         | Coordinates for this address                                                                             |
| » latitude         | float            | false    | none         | Latitude                                                                                                 |
| » longitude        | float            | false    | none         | Longitude                                                                                                |

### Product <a href="#tocs_product" id="tocs_product"></a>

```
{
  "id": "db050bb1-810d-4420-a6fb-c1ce472a4ca9",
  "name": "Mug Commanders Act",
  "description": "White stoneware mug with C-Handle is the perfect cup for any beverage",
  "category_1": "Home",
  "category_2": "Kitchen",
  "category_3": "Accessories",
  "category_4": "Containers",
  "category_5": "Mugs",
  "tags": [
    "mugs",
    "handle",
    "white",
    "brand"
  ],
  "condition": "new",
  "availability": "in_stock",
  "availability_date": "2019-02-06T17:41:31.427+01:00",
  "expiration_date": "2019-02-06T17:41:31.427+01:00",
  "price": 10,
  "sale_price": 8,
  "currency": "EUR",
  "image_link": "https://commandersact.com/images/shopping/mug_hi_res.jpg",
  "link": "https://commandersact.com/shopping/mug",
  "brand": "Commanders Act",
  "width": 6.4,
  "length": 7.3,
  "height": 9.5,
  "weight": 80.7,
  "size": "medium",
  "colors": [
    "white",
    "red"
  ],
  "gtin": "134588842456789000",
  "mpn": "134588842",
  "custom": {
    "internal_category_id": 721,
    "warehouse": "building B",
    "box_barcode": 1830135586179
  }
}
```

There are three ways to have product information in your conversion items. First method is to put product properties inline for each conversion item. Second method is to synchronize your product catalog with our database using "POST /products/bulk" endpoint and only send product ids in conversion items (our server will copy product properties from catalog). Third method is a combination of previous ones and implies having a product catalog and send the product information inline. In case a property is present in both catalog product and inline product, properties from inline product will overwrite properties from catalog. This method is useful when product information is incomplete or complementary in inline products. It is recommended to send products inline, except when you do not have all product information. In most cases you don't need to use the catalog. It is recommended to use as many fields as you can in order to be able to build good segments with advanced conditions. When you only send the id of the product in a conversion item, you need to make sure that your catalog already contains the product, otherwise product properties will not be added to your conversion item.

#### Properties <a href="#properties" id="properties"></a>

| Name               | Type                   | Required | Restrictions | Description                                                                                                                                                                                                                                               |
| ------------------ | ---------------------- | -------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                 | string(1-50)           | true     | none         | Unique identifier for the article (try using the most specific identifier or SKU), such as a reference. If there are several occurrences for the same identifier, only the last one will be recorded                                                      |
| name               | string(1-500)          | false    | none         | Name of the article                                                                                                                                                                                                                                       |
| description        | string(max 5000 chars) | false    | none         | Description of the article                                                                                                                                                                                                                                |
| category\_1        | string(1-250)          | false    | none         | Main category of the article                                                                                                                                                                                                                              |
| category\_2        | string(1-250)          | false    | none         | Second sub-category of the article                                                                                                                                                                                                                        |
| category\_3        | string(1-250)          | false    | none         | Third sub-category of the article                                                                                                                                                                                                                         |
| category\_4        | string(1-250)          | false    | none         | Fourth sub-category of the article                                                                                                                                                                                                                        |
| category\_5        | string(1-250)          | false    | none         | Fifth sub-category of the article. If you have more than five levels of category you may choose to concatenate the remaining ones like 'Bikes/Parts/Wheels/Front' or simply ignore the remaining ones like 'Bikes', depending on your segmentation needs. |
| tags               | \[string]              | false    | none         | Array of tags for the product. Tags can be anything that labels the product: hand-made, eco-friendly, heat-resistant etc.                                                                                                                                 |
| condition          | string                 | false    | none         | Current status of the material in your store (see list of possible values below)                                                                                                                                                                          |
| availability       | string                 | false    | none         | Current availability of the item in your store. Make sure to indicate the availability of the item on your store page and keep it up to date (see list of possible values below)                                                                          |
| availability\_date | string(ISO-8601)       | false    | none         | Date when product became or will become available. See "Date formats" section above for a list of allowed formats.                                                                                                                                        |
| expiration\_date   | string(ISO-8601)       | false    | none         | Date when product became or will become unavailable. See "Date formats" section above for a list of allowed formats.                                                                                                                                      |
| price              | float                  | false    | none         | Default price for the article. In a conversion you can specify the real price at which the item was sold in case of sales, discounts etc.                                                                                                                 |
| sale\_price        | float                  | false    | none         | Default price for the article during sales periods. In a conversion you can specify the real price at which the item was sold in case of discounts                                                                                                        |
| currency           | string(ISO-4217)       | false    | none         | Currency used for given prices. Note that you have to use the same currency for products and conversions                                                                                                                                                  |
| image\_link        | string(url)            | false    | none         | URL of product image                                                                                                                                                                                                                                      |
| link               | string(url)            | false    | none         | URL to the website where you can buy the item                                                                                                                                                                                                             |
| brand              | string(1-250)          | false    | none         | Brand of the article                                                                                                                                                                                                                                      |
| width              | float                  | false    | none         | Width of the article in centimeters (cm)                                                                                                                                                                                                                  |
| length             | float                  | false    | none         | Length of the article in centimeters (cm)                                                                                                                                                                                                                 |
| height             | float                  | false    | none         | Height of the article in centimeters (cm)                                                                                                                                                                                                                 |
| weight             | float                  | false    | none         | Height of the article in centimeters (grams)                                                                                                                                                                                                              |
| size               | string(1-250)          | false    | none         | Size of the article when width, height and lengts are not applicable. You can use any value that describes the size. Examples: S, XL, large                                                                                                               |
| colors             | \[string]              | false    | none         | Colors of product                                                                                                                                                                                                                                         |
| gender             | string(1-250)          | false    | none         | Gender for gender specific products (male, female, unisex)                                                                                                                                                                                                |
| gtin               | string(1-250)          | false    | none         | International trade identification number of the article Supported numbers: UPC (North America, 12 digits), EAN (Europe, 13 digits), JAN (Japan, 8 to 13 digits), ISBN (books, 13 digits)                                                                 |
| mpn                | string(1-250)          | false    | none         | Manufacturer part number of the material                                                                                                                                                                                                                  |
| custom             | object                 | false    | none         | Object containing custom properties                                                                                                                                                                                                                       |

**Enumerated Values**

| Property     | Value          |
| ------------ | -------------- |
| condition    | new            |
| condition    | refurbished    |
| condition    | used           |
| availability | in\_stock      |
| availability | available      |
| availability | pre\_order     |
| availability | out\_of\_stock |
| gender       | male           |
| gender       | female         |
| gender       | unisex         |
