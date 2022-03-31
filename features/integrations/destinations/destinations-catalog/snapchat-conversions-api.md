# Snapchat Conversions API

The Snapchat Conversions API allows you to pass web, app, and offline events to Snap via a server-side integration.

More details [here](https://marketingapi.snapchat.com/docs/conversion.html#introduction).

A **pixel ID** is requested for this destination, please find [here](https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en\_US) how to retrieve this value.

### Default Mappings to Snapchat Standard Events&#x20;

| COMMANDERS ACT EVENTS | SNAPCHAT STANDARD EVENT |
| --------------------- | ----------------------- |
| `begin_checkout`      | `START_CHECKOUT`        |
| `purchase`            | `PURCHASE`              |
| `add_to_cart`         | `ADD_CART`              |
| `view_item`           | `VIEW_CONTENT`          |
| login                 | `LOGIN`                 |
| `search`              | `SEARCH`                |
| `add_to_wishlist`     | `ADD_TO_WISHLIST`       |
| `page_view`           | `PAGE_VIEW`             |

### Default Mappings to Snapchat Custom Events&#x20;



| COMMANDERS ACT EVENTS | SNAPCHAT CUSTOM EVENT |
| --------------------- | --------------------- |
| `add_payment_info`    | `ADD_PAYMENT_INFO`    |
| `add_shipping_info`   | `ADD_SHIPPING_INFO`   |
| `generate_lead`       | `GENERATE_LEAD`       |
| `refund`              | `REFUND`              |
| `remove_from_cart`    | `REMOVE_FROM_CART`    |
| `select_content`      | `SELECT_CONTENT`      |
| `select_item`         | `SELECT_ITEM`         |
| `sign_up`             | `SIGN_UP`             |
| `view_cart`           | `VIEW_CART`           |
| `view_item_list`      | `VIEW_ITEM_LIST`      |
