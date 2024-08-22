# Browser-side events setup

Commanders Act Events Triggers are onsite events that are used by Commanders Act users to dynamically execute Tags.

### Definitions

| Metric                 | Description                                                                                                 |
| ---------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Trigger Label**      | Label for an event that is used by Commanders Act users to execute Tags. e.g. add\_to\_basket               |
| **Trigger Data Layer** | A JavaScript object that can be accessed by Tags that are executed on the related Trigger. e.g. product\_id |

### Installation

Commanders Act allows to set up common Trigger automatically without the involvement of technical team (e.g. _Container loaded_, _DOM ready_ or _Vertical Scroll 25%_). In cases where the default Triggers are not sufficient it is possible for technical personnel to implement custom Triggers. The necessary Trigger are defined during the Commanders Act setup process, but you can find a list of native Trigger on [this page](../user-guides-for-browser-side-platform/tags/rules/triggers.md).

To install a custom Trigger on the website it is necessary to call a JavaScript function with the following pattern:

```javascript
tC.event.{{ Trigger Label }}(this, {{ Trigger Data Layer }});
```

A typical example is an _Add to basket_ event where the product id of the selected product is sent with the event:

```javascript
tC.event.add_to_basket(this, { product_id: "12345" });
```

{% hint style="info" %}
#### Trigger Data Layer Properties

A common approach for the Trigger Data Layer is to always use the same properties like `event_label`, `event_type` and `event_value`—so in case of an `add_to_basket` Trigger the `event_value` would hold the product id of the selected product and in case of a `video_play` event the `event_value` would hold the current position within the video timeline. This allows to avoid to create multiple custom variable names for each individual event and therefore makes Trigger more generic.
{% endhint %}

{% hint style="warning" %}
#### Trigger Error Handling

In some situations it might happen, that a user interacts with a custom Trigger before the Commanders Act Web Container file was loaded. In this case using the Trigger function would cause a JavaScript `ReferenceError`. Therefore it is recommended to check the availability of the Trigger function before using it.

```javascript
if (tC && tC.event && typeof tC.event.add_to_basket === "function") {
    tC.event.add_to_basket(this, { product_id: "12345" });
}
```
{% endhint %}

### Testing

#### Via Quality Assurance Tag

The Tag template _Commanders Act - Event QA_ in the Commanders Act Tag library automatically outputs event Data Layer information to the JavaScript console when executed. Assigning this Tag with the Trigger allows to log a snapshot of the Data Layer when the respective Trigger is executed.\
\
Another way, more technical: you can type in your console tc\_arrray\_events when the event is executed. The Data Layer of the event variables will be displayed.
