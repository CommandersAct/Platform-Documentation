# Ecommerce/retail events

The following events are recommended for retail and ecommerce apps and websites. To learn how to implement these events for your website, refer to the [developer documentation](broken-reference).

{% hint style="info" %}
Retail and ecommerce apps should log the events listed in this article _**and**_ the events for **all apps**. Logging events along with their prescribed parameters ensures maximum available detail in reports and lets you benefit from the latest features and integrations as they become available.
{% endhint %}

| Event             | Trigger                                               | Parameters                                                                                      |
| ----------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| add_payment_info  | when a user submits their payment information         | coupon, currency, items, payment_type, value                                                    |
| add_shipping_info | when a user submits their shipping information        | coupon, currency, items, shipping_tier, value                                                   |
| add_to_cart       | when a user adds items to cart                        | currency, items, value                                                                          |
| add_to_wishlist   | when a user adds items to a wishlist                  | currency, items, value                                                                          |
| begin_checkout    | when a user begins checkout                           | coupon, currency, items, value                                                                  |
| generate_lead     | when a user submits a form or request for information | value, currency                                                                                 |
| purchase          | when a user completes a purchase                      | affiliation, coupon, currency, items, transaction_id, shipping, tax, value (required parameter) |
| refund            | when a refund is issued                               | affiliation, coupon, currency, items, transaction_id, shipping, tax, value                      |
| remove_from_cart  | when a user removes items from a cart                 | currency, items, value                                                                          |
| select_item       | when an item is selected from a list                  | items, item_list_name, item_list_id                                                             |
| select_promotion  | when a user selects a promotion                       | items, promotion_id, promotion_name, creative_name, creative_slot, location_id                  |
| view_cart         | when a user views their cart                          | currency, items, value                                                                          |
| view_item         | when a user views an item                             | currency, items, value                                                                          |
| view_item_list    | when a user sees a list of items/offerings            | items, item_list_name, item_list_id                                                             |
| view_promotion    | when a promotion is shown to a user                   | items, promotion_id, promotion_name, creative_name, creative_slot, location_id                  |
| page_view         | When a user view a page                               | type, name                                                                                      |
