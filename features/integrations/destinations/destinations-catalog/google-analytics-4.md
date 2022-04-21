# Google Analytics 4

Send events to the latest version of Google Analytics.\
Server-side data will be sent to [Google’s Measurement Protocol API](https://developers.google.com/analytics/devguides/collection/protocol/ga4).

## How to configure Google Analytics 4

Information needed:

### API secret

An "API Secret" that is generated through the Google Analytics UI. To create a new "API Secret", navigate in the Google Analytics UI to: \
Admin > Data Streams > choose your stream > Measurement Protocol > Create.

### Measurement ID

The identifier for a Data Stream. Found in the Google Analytics UI under: \
Admin > Data Streams > choose your stream > Measurement ID.

### Client ID Cookie Name

Cookie name holding the GA "Client ID" that uniquely identifies a user instance of a web client.

## Default Mappings to Google Analytics Standard Events

| COMMANDERS ACT EVENTS | GOOGLE STANDARD EVENT |
| --------------------- | --------------------- |
| `begin_checkout`      | `begin_checkout`      |
| `purchase`            | `purchase`            |
| `add_to_cart`         | `add_to_cart`         |
| `view_item`           | `view_item`           |
| `view_item_list`      | `view_item_list`      |
| `search`              | `search`              |
| `add_payment_info`    | `add_payment_info`    |
| `add_to_wishlist`     | `add_to_wishlist`     |
| `generate_lead`       | `generate_lead`       |
| `refund`              | `refund`              |
| `page_view`           | `page_view`           |

## Limitations

The following [limitations](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/limitations) apply to the Measurement Protocol for Google Analytics 4:

* `user_id` requires _both_ client-side and Measurement Protocol events to include the `user_id`.
* session data is not supported.
