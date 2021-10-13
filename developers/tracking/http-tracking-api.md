# HTTP tracking API

The HTTP Tracking API lets you record user data from any website or application. Requests are routed to our servers, and your data is routed to any destination you desire.

### Event API <a href="track" id="track"></a>

You may use the event API to capture the actions that your users perform. Every action results in what is known as an "event," which have associated properties. 

You should keep track of activities that are indications of your app's performance, such as Signed Up, Item Purchased, and Article Bookmarked. To begin, we recommend tracking only a few key events. More may easily be added later!

Example `event` call:

```c
POST https://collect.commander1.com/events?tc_s={id_site}
```

```json
{
  "event": "add_to_cart",
  "properties": {
      "value": 8.00,
      "currency": 'EUR',
      "items": [{
        "id": 'SKU_12345',
        "quantity": 1,
        "variant": 'red',
        "coupon": 'CHRISTMAS',
        "discount": 1.99,
        "product":{
          "id": '12345',
          "name": 'Trex tshirt',
          "category_1": 'clothes',
          "category_2": 't-shirts',
          "category_3": 'boy',
          "brand": 'Lacoste',
          "price": 9.99
        }
      }]
    }
}
```

Find details on **best practices in event naming** as well as the **`event` method payload** in our [Spec](about-events/).
