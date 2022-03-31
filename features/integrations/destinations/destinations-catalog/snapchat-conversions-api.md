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
