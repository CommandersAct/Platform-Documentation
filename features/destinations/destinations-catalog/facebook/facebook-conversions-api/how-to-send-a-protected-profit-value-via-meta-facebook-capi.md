# How to – Send a Protected Profit Value via Meta (Facebook CAPI)

### 🎯 Objective

"Value Optimization for Profit" from Meta allows campaigns to optimize based on order-level profitability rather than purchase value.

This is particularly relevant when product margins vary significantly and are not directly correlated with sale price.

{% hint style="info" %}
Value Optimization for Profit is currently available through Meta’s managed partner program and is not yet generally available to all advertisers.

If you are interested in enabling this feature, please reach out to your Meta representative.
{% endhint %}

Meta allows you to optimize campaigns using a business value through the parameter:

👉 **`net_revenue`**

However, many advertisers prefer **not to send their raw margin**, as it is highly strategic data.

👉 The goal is to:

* **avoid exposing your real margin**
* while still sending a **signal that Meta can use for optimization**

To achieve this, we will create a derived property:

👉 **`protected_profit_value`**

This value will be used instead of your raw margin in Meta CAPI.

{% hint style="warning" %}
This approach should be considered as **profit value indexing**, not irreversible anonymization.

It prevents the raw margin from being sent directly to Meta, but if someone has access to both the original margin and the indexed value for the same event, the transformation logic may theoretically be inferred.
{% endhint %}

***

### ⚠️ Prerequisites

Before implementing the transformation, make sure the following are in place:

#### 1. Margin availability in your data

You need to have access to your margin, or net revenue, in your data.

👉 This is typically done via a **product catalog import**, where margin is included as a product attribute.

#### 2. Event enrichment, Purchase events

Your `purchase` events must be enriched with this margin information.

👉 This is usually done via an **event enrichment setup**, matching the product ID in the event with your catalog data.

📖 Documentation:\
https://doc.commandersact.com/features/data-quality/enrichment

#### 3. Order-level profit

Meta’s optimization model is designed to work with profit at the order level.

If your margin is only available at product level, for example via catalog, you should ensure that a consistent order-level profit is available in your purchase events.

This can be done by using **Data Cleansing** in concert with **event enrichment**.

A common setup is:

* import product-level margin through a product catalog
* enrich the `purchase` event by matching event item IDs with catalog product IDs
* use a Data Cleansing formula to aggregate item-level margins into a consistent order-level profit value
* use this order-level profit value as the source for `protected_profit_value`

👉 The value used in the transformation should represent the total profit of the purchase event.

***

### 🧩 Step 1 – Create a Data Cleansing transformation, recommended

👉 It is strongly recommended to define the transformation in **Data Cleansing**, so that:

* the logic is centralized
* it can be reused across multiple destinations, other CAPIs, analytics, etc.
* it is easier to maintain

#### Steps

1. Go to **Data Quality > Data Cleansing**
2. Create a new transformation
3. Define a new property:

👉 `protected_profit_value`

***

### ⚙️ Suggested transformation approaches

Meta recommends sending transformed values in proportion to their exact ratio and avoiding approximation where possible.

This is important because Meta’s Value Optimization model is based on a regression model that predicts expected value. Therefore, magnitude matters, not only ordering.

In other words:

* preserving ordering means: higher profit → higher value
* preserving ratios means: if one purchase is twice as profitable, the value sent to Meta should also be twice as high

👉 Meta recommends preserving exact ratios between profit values.

This is why a proportional transformation is the safest approach for optimal performance.

The more the transformation deviates from a proportional index, the stronger the obfuscation may become, but the more it can distort Meta’s optimization signal.

Below are three possible approaches.

***

### 🟢 Option 1 – Proportional profit index, recommended by Meta

This is the recommended approach when optimization quality is the priority.

```sql
IF(NUMBER(net_revenue) > 0, NUMBER(net_revenue) * K, NULL)
```

Where:

* `net_revenue` is the raw order-level profit or margin.
* `K` is a client-specific secret indexing factor.
* `NULL` means that no `net_revenue` value should be sent for non-positive margins.

Example with `K = 37.48291`:

```sql
IF(NUMBER(net_revenue) > 0, NUMBER(net_revenue) * 37.48291, NULL)
```

#### How it works

The margin is multiplied by a client-specific indexing factor.

Example:

* $10 → 374.8291
* $20 → 749.6582
* $40 → 1499.3164

👉 Result:

* exact ratios are preserved
* Meta receives a clean value optimization signal
* the raw margin is not sent directly
* Ads Manager reporting remains meaningful if you know the indexing factor

#### Why this is recommended

This approach preserves the exact relative distances between profit values.

Example:

* $20 is 2× $10
* $40 is 4× $10

After transformation:

* 749.6582 is 2× 374.8291
* 1499.3164 is 4× 374.8291

👉 This is fully aligned with Meta’s recommendation.

{% hint style="info" %}
This approach provides confidential indexing, not irreversible anonymization.

If someone has access to both the original margin and the indexed value for the same event, the factor `K` may theoretically be inferred.
{% endhint %}

***

### 🟠 Option 2 – Offset profit index, advanced obfuscation

This approach can be used when the advertiser wants stronger obfuscation and accepts a controlled distortion of the optimization signal.

```sql
IF(NUMBER(net_revenue) > 0, (NUMBER(net_revenue) + C) * K, NULL)
```

Where:

* `K` is a client-specific secret indexing factor
* `C` is a small client-specific offset
* `C` should remain small compared with the smallest meaningful positive margin

Example:

```sql
IF(NUMBER(net_revenue) > 0, (NUMBER(net_revenue) + 0.75) * 37.48291, NULL)
```

#### How it works

The margin is first increased by a small offset, then multiplied by a client-specific indexing factor.

Example with `C = 0.75` and `K = 37.48291`:

* $10 → 402.9418
* $20 → 777.7709
* $40 → 1527.4286

👉 Result:

* the values are harder to interpret than a simple proportional factor
* the signal remains close to proportional if `C` is small
* however, exact ratios are no longer perfectly preserved

#### Important limitation

Adding `C` distorts ratios.

Example with `C = 5`:

* real ratio: $100 / $10 = 10
* transformed ratio: ($100 + 5) / ($10 + 5) = 7

👉 Meta receives a lower contrast between high-profit and low-profit purchases than the real one.

This can reduce optimization quality, especially when `C` is large compared with low positive margins.

#### Recommended rule for C

As a rule of thumb:

```
C should not exceed 5% to 10% of the smallest meaningful positive margin.
```

Example:

If the smallest meaningful positive margin is $10:

* conservative `C`: $0.50
* upper range `C`: $1.00

{% hint style="warning" %}
This option is not the approach recommended by Meta for optimal performance, because it does not preserve exact ratios.

Use it only when the advertiser explicitly accepts a trade-off between stronger obfuscation and potential optimization impact.
{% endhint %}

***

### 🔴 Option 3 – Bucketed profit score, maximum obfuscation, not recommended by Meta

This approach uses broader value bands to make reverse interpretation more difficult.

It should only be used when confidentiality constraints are stronger than performance requirements.

```sql
IF(NUMBER(net_revenue) <= 0, NULL,
  IF(NUMBER(net_revenue) < 5, 40,
    IF(NUMBER(net_revenue) < 15, 120,
      IF(NUMBER(net_revenue) < 30, 220, 320)
    )
  )
)
```

#### How it works

The margin is transformed into broader value bands.

Example:

* $3 → 40
* $10 → 120
* $25 → 220
* $40+ → 320

👉 Result:

* the original margin is much harder to reconstruct
* values are no longer proportional
* many different margins receive the same value
* the optimization signal is reshaped

#### Why this is not recommended by Meta

This approach preserves ordering, but it does not preserve exact ratios.

Example:

* $10 and $14 both become 120
* $15 and $29 both become 220
* $40 and $400 both become 320

This creates several issues:

* differences inside a bucket are lost
* artificial jumps are created between buckets
* high-margin purchases may be underrepresented
* low-margin purchases may be overrepresented
* Meta’s regression model receives a distorted value signal

{% hint style="danger" %}
Meta recommends avoiding shaping layers such as capping, compression, bucketing or threshold-based scoring when the goal is optimal Value Optimization performance.

This option is available as a maximum obfuscation strategy, but it may significantly reduce optimization quality.
{% endhint %}

***

### 📊 Summary of the three options

| Option                               | Formula                | Meta alignment | Obfuscation level | Performance risk |
| ------------------------------------ | ---------------------- | -------------: | ----------------: | ---------------: |
| Option 1 – Proportional profit index | `margin × K`           |      Excellent |            Medium |              Low |
| Option 2 – Offset profit index       | `(margin + C) × K`     |        Partial |           Medium+ |    Low to medium |
| Option 3 – Bucketed profit score     | `margin range → score` |           Poor |              High |   Medium to high |

👉 Recommended default:

```sql
IF(NUMBER(net_revenue) > 0, NUMBER(net_revenue) * K, NULL)
```

👉 Use Option 2 only when the advertiser wants additional obfuscation and accepts a controlled distortion.

👉 Use Option 3 only when confidentiality is more important than optimal performance.

***

### ⚠️ Handling zero or negative margins

For zero or negative margin values, Meta has not yet provided final guidance for negative values.

Until final guidance is available, the safest approach is to omit `net_revenue` for non-positive margins.

Recommended logic:

```sql
IF(NUMBER(net_revenue) > 0, NUMBER(net_revenue) * K, NULL)
```

When `net_revenue` is omitted:

* the event is still tracked as a Purchase conversion
* the event is not used for profit optimization
* the event does not count toward the 200-conversion eligibility threshold

{% hint style="warning" %}
Make sure that returning `NULL` in your transformation effectively prevents the `net_revenue` field from being sent.

If your implementation still sends the field with a null or empty value, adapt the mapping logic so that `net_revenue` is omitted for non-positive margins.
{% endhint %}

***

### 📈 Impact on Ads Manager reporting

Ads Manager will report the indexed values sent to Meta, not the original profit margins.

Example:

If you send:

```
protected_profit_value = profit_margin × 10
```

Then Ads Manager reporting will reflect values multiplied by 10.

This means that reporting remains meaningful as long as the advertiser knows the indexing factor.

{% hint style="info" %}
ROAS or margin-related reporting in Ads Manager should be interpreted as indexed reporting, not raw profit reporting.
{% endhint %}

***

### 🔗 Step 2 – Map the value in Meta CAPI

In your **Facebook Conversions API destination**:

1. Open your destination configuration
2. Go to the **Smart Mapping** section
3. Map the following:

👉 **`net_revenue` → `protected_profit_value`**

4. Also make sure:

* `currency` is properly mapped

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
* without exposing your raw margin directly

👉 Meta can:

* optimize campaigns based on expected profit value
* use the indexed value as a value optimization signal

👉 But your strategic data:

* is not sent in its original form
* is protected through a client-specific transformation
* is not directly readable as a raw margin

The value sent via `net_revenue` will be used by Meta for both optimization and reporting.

{% hint style="warning" %}
The value reported in Ads Manager is the indexed value sent to Meta, not the original raw margin.
{% endhint %}

***

### 💡 Best practices

* Use Option 1 by default
* Keep the transformation stable over time
* Use a client-specific, non-obvious `K`
* Avoid round factors such as `10`, `100` or `1000` when possible
* Avoid capping, compression, bucketing or threshold-based scoring if optimization quality is the priority
* If using Option 2, keep `C` very small compared with the smallest meaningful positive margin
* If using Option 3, clearly validate that the advertiser accepts the potential performance trade-off
* Omit `net_revenue` for non-positive margins until Meta provides final guidance
* Reuse this transformation for:
  * other CAPIs, TikTok, Snap, etc.
  * analytics platforms
  * internal reporting proxies
