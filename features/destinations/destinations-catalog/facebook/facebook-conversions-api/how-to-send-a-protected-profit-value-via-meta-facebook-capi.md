# How to – Send a Protected Profit Value via Meta (Facebook CAPI)

### 🎯 Objective

Meta’s Value Optimization for Profit allows campaigns to optimize based on order-level profitability rather than purchase value.

This is particularly relevant when product margins vary significantly and are not directly correlated with sale price.

{% hint style="info" %}
Value Optimization for Profit is currently available through Meta’s managed partner program and is not yet generally available to all advertisers.

If you are interested in enabling this feature, please reach out to your Meta representative.
{% endhint %}

\
Meta allows you to optimize campaigns using a business value through the parameter:

👉 **`net_revenue`**

However, many advertisers prefer **not to send their raw margin**, as it is highly strategic data.

👉 The goal is to:

* **avoid exposing your real margin**
* while still sending a **signal that Meta can use for optimization**

To achieve this, we will create a derived property:

👉 **`protected_profit_value`**

This value will be used instead of your raw margin in Meta CAPI.

***

### ⚠️ Prerequisites

Before implementing the transformation, make sure the following are in place:

#### 1. Margin availability in your data

You need to have access to your margin (or net revenue) in your data.

👉 This is typically done via a **product catalog import**, where margin is included as a product attribute.

#### 2. Event enrichment (Purchase events)

Your `purchase` events must be enriched with this margin information.

👉 This is usually done via an **event enrichment setup**, matching the product ID in the event with your catalog data.

📖 Documentation:\
https://doc.commandersact.com/features/data-quality/enrichment

#### 3. Order-level profit

Meta’s optimization model is designed to work with profit at the order level.

If your margin is only available at product level (e.g. via catalog), you should ensure that a consistent order-level profit is available in your purchase events.

This can be done by:

* computing it on your backend before sending the event, or
* aggregating item-level margins into an order-level value with a formula inside Commanders Act platform

👉 The value used in the transformation should represent the total profit of the purchase event.

***

### 🧩 Step 1 – Create a Data Cleansing transformation (recommended)

👉 It is strongly recommended to define the transformation in **Data Cleansing**, so that:

* the logic is centralized
* it can be reused across multiple destinations (other CAPIs, analytics, etc.)
* it is easier to maintain

#### Steps

1. Go to **Data Quality > Data Cleansing**
2. Create a new transformation
3. Define a new property:

👉 `protected_profit_value`

***

### ⚙️ Suggested transformation approaches

Meta supports sending transformed values as long as the optimization signal remains consistent and logically aligned with profitability.

In particular, preserving value ordering (higher profit → higher value) is key. More advanced transformations may reshape the signal and should be tested carefully.\
\
Below are two suggested approaches to generate a protected profit signal.

***

#### 🟢 Option 1 – Balanced (recommended)

This approach provides a good balance between:

* preserving optimization performance
* reducing direct readability of the margin

```sql
IF(NUMBER(net_revenue) <= 0, 0,
  IF(NUMBER(net_revenue) >= 40, 100, NUMBER(net_revenue) * 2.5)
)
```

#### How it works

* The margin is scaled and capped
* Example:
  * $10 → 25
  * $20 → 50
  * $40+ → 100

👉 Result:

* Meta receives a consistent and ordered value signal
* The raw margin is not shared in its original form

***

#### 🟡 Option 2 – Enhanced protection

This approach uses broader value levels to make reverse interpretation more difficult, while preserving profitability ordering.

```sql
IF(NUMBER(net_revenue) <= 0, 0,
  IF(NUMBER(net_revenue) < 5, 40,
    IF(NUMBER(net_revenue) < 15, 120,
      IF(NUMBER(net_revenue) < 30, 220, 320)
    )
  )
)
```

#### How it works

* The margin is transformed into broader value bands
* Example:
  * $3 → 40
  * $10 → 120
  * $25 → 220
  * $40+ → 320

👉 Result:

* Maintains profitability ordering
* Makes the original margin less directly readable
* Provides stronger obfuscation than a simple scaled value

Note: this approach introduces a more abstract representation compared to a continuous profit value and may slightly reshape the optimization signal.

***

### 💡 Notes

* Both approaches preserve **value ordering**, which is key for optimization
* The first approach is closer to a linear transformation and may provide a more stable signal
* The second approach provides stronger obfuscation, but slightly reshapes the value distribution

👉 You can adapt thresholds and factors based on your business, as long as:

* higher margin → higher value
* the transformation remains consistent over time

***

### ⚙️ Alternative – Transformation inside the destination

👉 You can also define the transformation directly in:

**Destination settings → Properties transformation**

However, this is less recommended because:

* the logic is not reusable
* it is duplicated per destination

👉 Use this approach only for quick tests or specific cases.

***

### ✅ Result

You are sending to Meta:

* a **profit-based optimization signal**
* without exposing your raw margin

👉 Meta can:

* rank products
* optimize campaigns

👉 But your strategic data:

* is not sent in its original form
* is not directly interpretable

***

### 💡 Best practices

* Keep the transformation **consistent over time**
* Ensure it remains **monotonic** (higher margin → higher value)
* Adjust thresholds (5, 15, 30…) based on your business
* Reuse this transformation for:
  * other CAPIs (TikTok, Snap, etc.)
  * analytics platforms
  * internal reporting proxies
