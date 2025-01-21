# Ecommerce/retail events

The following events are recommended for retail and ecommerce apps and websites. To learn how to implement these events for your website, refer to the [developer documentation](../events-reference/).

{% hint style="info" %}
Retail and ecommerce apps should log the events listed in this article _**and**_ the events for **all apps**. Logging events along with their prescribed parameters ensures maximum available detail in reports and lets you benefit from the latest features and integrations as they become available.
{% endhint %}

| [add\_payment\_info](../events-reference/#add\_payment\_info)   | when a user submits their payment information         | coupon, currency, items, payment\_type, value                                                    |
| --------------------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| [add\_shipping\_info](../events-reference/#add\_shipping\_info) | when a user submits their shipping information        | coupon, currency, items, shipping\_tier, value                                                   |
| [add\_to\_cart](../events-reference/#add\_to\_cart)             | when a user adds items to cart                        | currency, items, value                                                                           |
| [add\_to\_wishlist](../events-reference/#add\_to\_wishlist)     | when a user adds items to a wishlist                  | currency, items, value                                                                           |
| [begin\_checkout](../events-reference/#begin\_checkout)         | when a user begins checkout                           | coupon, currency, items, value                                                                   |
| [generate\_lead](../events-reference/#generate\_lead)           | when a user submits a form or request for information | value, currency                                                                                  |
| [purchase](../events-reference/#purchase)                       | when a user completes a purchase                      | affiliation, coupon, currency, items, transaction\_id, shipping, tax, value (required parameter) |
| [refund](../events-reference/#refund)                           | when a refund is issued                               | affiliation, coupon, currency, items, transaction\_id, shipping, tax, value                      |
| [remove\_from\_cart](../events-reference/#remove\_from\_cart)   | when a user removes items from a cart                 | currency, items, value                                                                           |
| [select\_item](../events-reference/#select\_item)               | when an item is selected from a list                  | items, item\_list\_name, item\_list\_id                                                          |
| select\_promotion                                               | when a user selects a promotion                       | items, promotion\_id, promotion\_name, creative\_name, creative\_slot, location\_id              |
| [view\_cart](../events-reference/#view\_cart)                   | when a user views their cart                          | currency, items, value                                                                           |
| [view\_item](../events-reference/#view\_item)                   | when a user views an item                             | currency, items, value                                                                           |
| [view\_item\_list](../events-reference/#view\_item\_list)       | when a user sees a list of items/offerings            | items, item\_list\_name, item\_list\_id                                                          |
| view\_promotion                                                 | when a promotion is shown to a user                   | items, promotion\_id, promotion\_name, creative\_name, creative\_slot, location\_id              |
| [page\_view](../events-reference/#page\_view)                   | When a user view a page                               | type, name                                                                                       |
