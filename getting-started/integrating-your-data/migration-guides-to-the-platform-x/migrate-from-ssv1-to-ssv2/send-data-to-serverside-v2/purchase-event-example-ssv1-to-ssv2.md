# Purchase event example (ssv1 to ssv2)

Here are an example of a serverside v1 hit : \
\
Booking Confirmation :

```json
{
    "method": "GET",
    "event_page_name_detailed": "page.Checkout.Confirmation",
    "booking_order_number": 9179124954957,
    "product_list_pricing_price_base_amount": 295.82,
    "product_list_pricing_currency_displayed": "USD",
    "event_page_funnel_location": 70,
    "event_page_product_line": "F",
    "point_of_sale_eg_brand_name": "magicOne",
    "privacy_ccpa_consent": true,
    "privacy_gdpr_consent": true,
    "product_list_product_id": 4521812,
    "request_request_url": "https://www.domain.com/Checkout/V1/MultiItemBookingConfirmation",
    "user_sha256_email_address": "4a0a303e33c11f496a9312a77309133325af1527a26d9d95cf74b81feba9c955",
    "device_information_user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36 Edg/96.0.1054.62",
    "timestamp": "11/01/2022 14:32",
 
}
```

It should be sent to the serverside v2 in this format (adding maximum of recommanded properties) :&#x20;

```json
{
    "event_name": "purchase",
    "properties": {
        "id": 9179124954957,
        "revenue":295.82,
        "value": 300.00,
        "currency": "USD",
        "lob": "F",
        "point_of_sale_eg_brand_name": "magicOne",
        "items": [...{ "product":{ "id":4521812}}],
        "name" : "page.Hotels.Checkout.Confirmation",
        "user": {
            "id": "61be2261-8701-4b4d-af97-60ea4329c7aa",
            "email_sha256": "4a0a303e33c11f496a9312a77309133325af1527a26d9d95cf74b81feba9c955",
            "consent_categories": [
                1,
                2,
                3
            ]
        }
    },
    "page": {
        "location": "https://www.domain.com/Checkout/V1/MultiItemBookingConfirmation"
    },
    "device": {
        "user_agent": "Mozilla/5.0 (X11; CrOS x86_64 14268.67.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.111 Safari/537.36",
        "cookie": "_fbp=fb.1.1596403881668.1116446470;_fbc=fb.1.233356.5656565;"
    },
    "event_timestamp": 1641907920000
}
```

### Standard parameters :&#x20;

{% hint style="warning" %}
Other standard recommanded parameters should be added to the purchase event, following the [purchase event documentation](https://community.commandersact.com/platform-x/developers/tracking/events-reference#purchase)
{% endhint %}

{% hint style="info" %}
_\_fbp and \_fbc_ cookies should be sent through the `cookie`parameter. It can also be sent in the `integrations.facebook parameter (ex : facebook.fbp:123)`
{% endhint %}

### Custom parameters :
