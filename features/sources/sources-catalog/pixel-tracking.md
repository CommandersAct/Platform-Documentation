# Pixel Tracking

Pixel Tracking, also known as 1x1 gifs, or clear gifs, lets you record data from any website (or application) **where JavaScript or POST requests are not allowed**, but where you can insert an image (aka GET hit)

{% hint style="info" %}
When a POST request is possible, please prefer the [http tracking API](http-tracking-api.md), more convenient to use.
{% endhint %}

## Basic Event Call

To send a basic event call using pixel tracking, construct a GET request to the tracking endpoint URL with the necessary query parameters. The following example demonstrates a basic event call for tracking a page view:

{% code fullWidth="false" %}
```c
GET  https://collect.commander1.com/events?tc_s={siteId}&token={yourSourceKey}&event_name=page_view&prop1=value1
```
{% endcode %}

In the above example, replace `{siteId}` with the ID of your site (aka workspace), `{yourSourceKey}` with your specific source key, and `value1` with the desired value for `prop1`. Remember to URL encode the string values, especially if they contain special characters or spaces.

## Event Call with Objects and Arrays

Pixel tracking allows for more complex data structures like objects and arrays. To include them in your event calls, you can nest parameters using the dot notation for objects and square brackets for arrays. The following example demonstrates an event call with objects and arrays:

```json
{
  "event_name": "page_view",
  "tc_s": "1234",
  "token": "abcdef",
  "page_type": "product_list",
  "page_name": "Best sellers",
  "user": {
    "id": "12356",
    "email": "toto@domain.fr",
    "consent_categories": [
      "1",
      "3"
    ]
  }
}
```

To transform the above JSON event call to URL parameter form, follow these steps:

1. Start with an empty string for the URL parameter form.
2. Copy the key-value pairs at the top level of the JSON object (`event_name`, `tc_s`, `token`, `page_type`, `page_name`) as they are, separating them with ampersands (`&`).
3. For nested objects like `user`, represent them in the URL parameter form by appending the nested key using square brackets (`[]`).
4. For array values like `user[consent_categories]`, append `[]` to the key to indicate an array parameter.
5. Include each element of the array as a separate key-value pair, appending the square brackets notation to the key as well.
6. URL encode the string values, such as replacing the space in `Best sellers` with `%20` and the `@` symbol in the email address with `%40`.

The transformed URL parameter form for the JSON event call would be:

{% code overflow="wrap" %}
```plaintext
GET  https://collect.commander1.com/events?tc_s=1234&token=abcdef&event_name=page_view&page_type=product_list&page_name=Best%20sellers&user[id]=12356&user[email]=toto%40domain.fr&user[consent_categories][]=1&user[consent_categories][]=3
```
{% endcode %}

## Manage array of objects (ex: items)

Arrays of objects can also be handled in pixel tracking event calls. This allows you to include multiple items within a single event, such as a purchase event. Let's consider an example of managing an array of objects for items in a purchase event:

```json
{
  "id": "O_12345",
  "revenue": 16.00,
  "value": 22.53,
  "shipping_amount": 3.33,
  "tax_amount": 3.20,
  "currency": "EUR",
  "user": {
    "id": "12356",
    "email": "toto@domain.fr"
  },
  "items": [
    {
      "id": "SKU_12345",
      "quantity": 1,
      "product": {
        "id": "12345",
        "name": "Trex tshirt",
        "category_1": "clothes",
        "colors": ["red"],
        "price": 9.99
      }
    },
    {
      "id": "SKU_12346",
      "quantity": 1,
      "price": 9.99,
      "product": {
        "id": "12346",
        "name": "Heart tshirt",
        "colors": ["blue", "white"],
        "price": 9.99
      }
    }
  ]
}
```

To include the array of objects within the event call, follow these steps:

1. Include the key-value pairs at the top level of the JSON object as usual (`id`, `revenue`, `value`, `shipping_amount`, `tax_amount`, `currency`, `user`).
2. For the array of objects, specify the key (e.g., `items`) and use square brackets (`[]`) to indicate an array parameter.
3. Include each object within the array as a separate set of key-value pairs, preserving the structure of the objects.
4. If necessary, nest additional objects or arrays within the objects of the array.

Example of transforming the JSON event call to URL parameter form:

{% code overflow="wrap" %}
```plaintext
id=O_12345&revenue=16.00&value=22.53&shipping_amount=3.33&tax_amount=3.20&currency=EUR&user[id]=12356&user[email]=toto%40domain.fr&items[0][id]=SKU_12345&items[0][quantity]=1&items[0][product][id]=12345&items[0][product][name]=Trex%20tshirt&items[0][product][category_1]=clothes&items[0][product][colors][]=red&items[0][product][price]=9.99&items[1][id]=SKU_12346&items[1][quantity]=1&items[1][price]=9.99&items[1][product][id]=12346&items[1][product][name]=Heart%20tshirt&items[1][product][colors][]=blue&items[1][product][colors][]=white&items[1][product][price]=9.99
```
{% endcode %}

In the transformed URL parameter form, each item within the array is represented by its index, followed by the keys and values of the nested object.
