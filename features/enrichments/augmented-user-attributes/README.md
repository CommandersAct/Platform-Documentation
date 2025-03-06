# Augmented User Attributes

## **What is an augmented user attribute?**

This feature allows you to create enriched properties on your user: flags, scores, ratio, rolling count/average, conditional value, boolean...

Enrich your data with your business rules in a user-friendly UI.

An enrichment transforms a property from a static value to a dynamic/enriched one.

By introducing business rules to your attributes, you give them context and more meaning. These enriched attributes then become the building blocks for dynamic segmentation, analytics, or can be retrieve in the datalayer via TagCommander to enrich your tags.

![](<../../../.gitbook/assets/Capture d’écran 2021-10-01 à 16.34.55.png>)

{% hint style="danger" %}
All augmented user attributes are not retroactive: it starts to count data from the creation date of the attribute.
{% endhint %}

## Flag

### Description

**Flag allows you to tag your customers** who met all the conditions you defined that are relevant to your business. It is helpful to create advanced segmentation based on criteria. You can tag your best customers or identify visitors who have an interest on your products but did not buy. Then you can create new segments based on these specific flags and mix it with more granular conditions (ex : have not seen a specific page within last 2h).

{% hint style="info" %}
What are the differences between segment and flag?
{% endhint %}

→ **Segments** can help you to identify and activate your customers based on their live behaviour: page views, clicks, sign-up, orders…\
Your customers are interacting with you, your websites, your applications, your customer service… you have to identify these live actions in order to prepare the next best action that will enhance your customer experience: for example onsite personalization after a click on a remarketing ad and a specific product view, personalized email after a contact with the customer service…\\

Segments are built for instant reaction :\
customer actions 〉identification 〉marketing activation\
Because of this, **segments are dynamic**. Your users, according to their actions, will dynamically enter and most importantly exit automatically your segments the second they no longer meet the conditions of the segment . You are sure to work on fresh data.

→ In a different way, **Flags** can help you to categorize your customers based on what really matter for your business: revenue.

You have to define which dimensions are key for your business and define a matrix that can help you to categorize your customers. For example, you want to flag your customers based on their order frequency and average order amount:

![](<../../../.gitbook/assets/image (10) (1) (2) (1) (1).png>)

However, you can go further with flags because you can integrate other dimensions such as period, online/offline purchase or whatever you need. This is allowed because there is no data retention for a flag, data is stored for a long time: the flag defined will not be removed on the user, except if you defined some exit conditions.

{% hint style="success" %}
As best practices, you should define around 10 different flags in order to categorize your customers and as many segments as you need.
{% endhint %}

{% hint style="danger" %}
**Important:**

The new flag defined is **NOT** retroactive (yet):
{% endhint %}

![](<../../../.gitbook/assets/image (9) (1) (2).png>)

Your new flag will take into consideration all the future actions/events/hits from the date you have created it.

{% hint style="info" %}
It will be possible soon to define retroactive flags. Stay connected!
{% endhint %}

### Popular use cases

* Flag _VIP customers:_ flag all your best customers
* Flag _window shoppers_: customers interested but not converted
* Review our [Business case](broken-reference/)

### Example

You would like to launch a fidelity program with different status for each customer: Platinum, Gold, Silver, Bronze… You have to define all characteristics for each status and then create flags in order to categorize your customers according to the criteria you decided.

For example:

* Platinum
  * Total amount orders over the last 6 months >800€
  * Number of visits over the last 6 months >6
  * …
* Gold
  * Total amount orders over the last 6 months 600€ < 800€
  * Number of visits over the last 6 months 4 < 6
  * …
* Silver
  * Total amount orders over the last 6 months 400€ < 600€
  * Number of visits over the last 6 months 2 < 4
  * …
* Bronze
  * Total amount orders over the last 6 months <400€
  * Number of visits over the last 6 months <2
  * …

Now it is your turn ;)

### How it works

1\. Name your new flag attribute and describe it

2\. Define your conditions to ADD the flag

Add conditions among these universes:

* For visitor
  * Filter among all the variables available through your web / mobile tracking
* For page-view
  * Specify the number of page view over a period
  * Specify other variables such as page name, product category…
* For view
  * Specify the number of views of your advertising over a period (all the advertising data comes from Mix Commander)
  * Specify other variables such as campaign, channel…
* For click
  * Specify the number of clicks on your advertising over a period (all the advertising data comes from Mix Commander)
  * Specify other variables such as campaign, channel…
* For conversion
  * Specify the number of conversions (orders, sign-up…) over a period
  * Specify other variables such as product name, billing information…

You can add multiple variables with the AND/OR function.

3\. Define your conditions to REMOVE the flag

* Never remove the flag
* Remove the flag IF all conditions defined to add the flag are no longer met
* Remove the flag IF specific conditions are met:

You can use the same conditions and filters as defined for adding the flag.

{% hint style="info" %}
Please keep in mind that segments are more powerful to manage entry and exit criteria because they are dynamics (no needs to set exit conditions).
{% endhint %}

## Rolling Sum / Average / Min / Max

### Description

Calculate cumulative sum, average, minimum or maximum for one variable based on a specific date range. It allows you to create new business rules based on a variable aggregation.

You can use these new indicators to create new segments or to flag your customers.

### Popular use cases

* Total order: cumulative total order amount for last 6 months
* Page views: total of pages views for last week
* Orders: Average orders amount for last 6 months
* Products: Average products in last month
* Orders: Minimum order amount for last 6 months
* Orders: Maximum order amount for last 6 months

### Example

You would like to identify customers who have ordered more than 300€ in the product category ‘clothes’ over the last 2 months. You set up the new rolling sum attribute:

|                                                                                                                                                                  | **Customer A**                                                                  | **Customer B**                                                                 |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Order #1**                                                                                                                                                     | <p>Product Category: Clothes</p><p>Price: 80€</p><p>Date: 3 months ago</p>      | <p>Product Category: Bag</p><p>Price: 80€</p><p>Date: 3 months ago</p>         |
| **Order #2**                                                                                                                                                     | <p>Product Category: Shoes</p><p>Price: 100€</p><p>Date: 2 months ago</p>       | <p>Product Category: Clothes</p><p>Price: 150€</p><p>Date: 1 month ago</p>     |
| **Order #3**                                                                                                                                                     | <p>Product Category: Clothes</p><p>Price: 150€</p><p>Date: 1 month ago</p>      | <p>Product Category: Clothes</p><p>Price: 200€</p><p>Date: 2 weeks ago</p>     |
| <p><strong>Rolling SUM</strong><br>‘Total orders amount clothes &#x3C;2 months’</p><p>Filters:</p><p>Product category = Clothes</p><p>Period = last 2 months</p> | <p><strong>150 €</strong></p><p>(only the order #3 fill all the conditions)</p> | <p><strong>350 €</strong></p><p>(Orders #2 and #3 fill all the conditions)</p> |
| <p><strong>Segment based on the new attribute</strong><br>‘Users with a total orders amount clothes &#x3C;2 months’</p><p>Filters:</p><p>Total >300€</p>         | **❌ No entry**                                                                  | \*\*\*\*:white\_check\_mark: **Entry**                                         |

You can now create a new segment based on the new attribute ‘\[total orders amount clothes <2 months] >300€’ which concerns, on this example, only the customer B.

With our example we can also calculate the average orders amount or the minimum / maximum amount.

### How it works

1\. Name your new attribute

2\. Specify the universe (page view, view, click, conversion) and the variable you want

{% hint style="warning" %}
Variable type: numeric only
{% endhint %}

3\. Define the date range you want

* Forever: no period defined, you consider all the dates
* Relative: you can set a duration on rolling hours or days (last 3 days for example)
* Absolute: data is aggregated from a specific date (from 01/09/2019 for example)

{% hint style="info" %}
Minimum period: 1 hour\
Maximum period: No limit
{% endhint %}

4\. \[Optional] If needed, define conditions in order to calculate the aggregation only if the conditions are met

## Rolling Count

### Description

Create a countdown attribute for one variable, based on a specific date range. This feature is helpful to define your best customers based on KPI like order frequency or number of visits on your website.

### Popular use cases

* Frequency: conversions number in last 6 months
* Discount efficiency: number of conversions with discount codes
* Cross-selling: number of conversions with more than 2 product categories.

### Example

You would like to segment users who have 2 or more conversions with a discount code.\
You set up the new rolling count attribute:\
Count \[Conversions] where \[Conversion discount code] = 'True'

|                                                                                                                                                          | **Customer A**                                                                                        | **Customer B**                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Order #1**                                                                                                                                             | <p>Product Category: Clothes</p><p>Price: 80€</p><p>Date: 3 months ago</p><p>Discount code: False</p> | <p>Product Category: Bag</p><p>Price: 80€</p><p>Date: 3 months ago</p><p>Discount code: True</p>      |
| **Order #2**                                                                                                                                             | <p>Product Category: Shoes</p><p>Price: 100€</p><p>Date: 2 months ago</p><p>Discount code: False</p>  | <p>Product Category: Clothes</p><p>Price: 150€</p><p>Date: 1 month ago</p><p>Discount code: False</p> |
| **Order #3**                                                                                                                                             | <p>Product Category: Clothes</p><p>Price: 150€</p><p>Date: 1 month ago</p><p>Discount code: True</p>  | <p>Product Category: Clothes</p><p>Price: 200€</p><p>Date: 2 weeks ago</p><p>Discount code: True</p>  |
| <p><strong>Rolling Count</strong><br>‘Total conversions with a discount code'</p><p>Filters:</p><p>Discount code = 'True'</p>                            | <p><strong>1</strong></p><p>(only the order #3 fill all the conditions)</p>                           | <p><strong>2</strong></p><p>(Orders #1 and #3 fill all the conditions)</p>                            |
| <p><strong>Segment based on the new attribute</strong><br>‘Users who have 2 or more conversions with a discount code'</p><p>Filters:</p><p>Total >=2</p> | **❌ No entry**                                                                                        | \*\*\*\*:white\_check\_mark: **Entry**                                                                |

Then you can create a segment with the rolling count attribute 'Users with total conversions with a discount code = 2 or more' which returns, on our example, only the customer B. However you can go further by adding a period or others conditions.

### How it works

1\. Name your new attribute

2\. Specify the universe (page view, view, click, conversion) you want

3\. Define the date range you want

* Forever: no period defined, you consider all the dates
* Relative: you can set a duration on rolling hours or days
* Absolute: data is aggregated from a specific date

{% hint style="info" %}
Minimum period: 1 hour\
Maximum period: No limit
{% endhint %}

4\. Define conditions in order to count only if the conditions are met

Filter on a specific page, product, ad…

## Calculus / Score

### Description

You can add, subtract, divide or multiply 2 or more variables, or create dynamic scores or incorporate conditional logic and complex formulas. These new calculated attributes can be part of a segmentation. This feature allows you to define new KPIs based on mathematical formulas.

### Popular use cases

* Dynamic Scoring: Assign scores to users based on specific conditions to enable targeted marketing strategies.
* Ratio: repartition online/offline conversions
* CLV: Customer Lifetime Value

### Examples

#### Simple Engagement Score:

Assign an engagement score to users based on recent activities, without overcomplicating the conditions. For instance:

> IF recent activity is 'purchase', set engagement score to 3.\
> IF recent activity is 'add\_to\_cart', set engagement score to 2.\
> IF recent activity is 'visited\_site', set engagement score to 1.
>
> Else, set engagement score to 0.

It will look like this in the interface:&#x20;

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**Warning**: Circular dependencies in formulas are not permitted. The system detects circular references and prevents the formula from being saved. For example, a formula where an attribute is defined to increment itself (e.g., you create a score with a name`attrs.toto and you create a formula like "attrs.toto + 1"`) Same for complex circular dependencies where attribute A depends on B, B depends on C, and C depends on A will be blocked.
{% endhint %}

#### Ratio:

You would like to identify cross-channel customers meaning the partition of customers who are buying both online and offline. You need a ratio between online and offline conversions:

> Channel ratio: number of online conversions / number of offline conversions

Higher is the rate, more the preferred channel is online and lower is the rate more the preferred channel is offline.

Customer Lifetime Value (CLTV):\
This metric helps you to estimate the income per customer during his entire relationship with your company (present and future). It allows you to establish forecasts on profits based on future cash flows.

> CLTV = Customer Value ✕ Customer Average Lifespan

> Customer Value = Average purchase value ✕ Average purchase frequency (on 1 year)

> Customer Average Lifespan depends on your business model (subscriptions service, freemium, retailer...). In general we consider the customer average lifespan is comprised between 1 and 3 years.

To sum-up, in order to calculate the customer lifetime value with the augmented user attributes feature, you have to:

1. Use a Rolling Average attribute to determine the average purchase value and the average purchase frequency
2. Use a Calculus attribute to define the Customer Value by multiplying the average purchase value and the average purchase frequency (determined previously on step 1)
3. Ultimately, use again a Calculus attribute to estimate the Customer Lifetime Value by multiplying the Customer Value (as calculated on step 2) and the Customer Average Lifespan (determined by your business model).

You can calculate the CLTV step by step or you can also create a formula that combines all the dimensions.

Ex:\
Average purchase value (on 1 year) = 50€\
Average purchase frequency (on 1 year) = 5 orders/year\
Customer Value = 250€ (50x5)\
Customer Average Lifespan = 2 years\
Customer Lifetime Value = 500€ (250x2)

Or: CLTV = (50x5)x2 = 500€

### How it works

1\. Name your new calculated attribute

2\. Specify the mathematic formula (rule) to calculate with the variables

{% hint style="warning" %}
Variable type: numeric only

Operators supported: ➕ ➖ ➗✖️
{% endhint %}

You have to type the variable name and add the operator. When a variable name is found, the autocompletion feature will suggest you the exact name.

Ex: type ‘Lab’ and the platform will suggest you ‘Label’.

## Copy

### Description

This feature allows you to copy values stored at the event level (pages, views, clicks, conversions) and paste to the user level. You can aggregate data at the user level in order to consolidate all the data around one unique user.

![](<../../../.gitbook/assets/image (7) (1) (1).png>)

![](<../../../.gitbook/assets/image (5) (1) (2).png>)New functionality: copy the data you need stored on all universes (pages, views, clicks and conversion) to the user level. As a result, the data will be stored for life (in respect with GDPR) and not deleted after 30 days (usually 30 days but depends on your contract).

It is useful to have a global view of dimensions such as product categories viewed or last order date.

### Popular use cases

* Last checkout date
* Product categories viewed

### Example

You are looking for a travel for your next holidays. You visit many websites, blogs, travel agencies websites... It takes time to choose the best offer that will suit you perfectly.

As a travel agency, you have many visitors on your website who left many informations such as trip dates, destinations... This online data will be stored 30 days, however your sales cycle could be long, more than 30 days. In order to don't loose this precious information, it could be useful to keep this data and this is what Copy allows you to do.

You can create a new attribute called 'Trip dates' and store the dates considered. You can do the same for 'destination' or whatever that could be useful for you. Then you can launch a dedicated campaign 3 months later with a segment based on this data (if there is no conversion for these customers).

![](<../../../.gitbook/assets/image (6) (2) (1).png>)

### How it works

1\. Name your new attribute

2\. Specify the universe (page view, view, click, conversion) and the variable you want

{% hint style="warning" %}
If a copy is from an encrypted variable, the attribute will be encrypted too
{% endhint %}

3\. Define the date range you want

* Forever: no period defined, you consider all the dates
* Relative: you can set a duration on rolling hours or days
* Absolute: data is aggregated from a specific date

{% hint style="info" %}
Minimum period: 1 hour\
Maximum period: No limit
{% endhint %}

4\. If needed, define conditions in order to copy the aggregation only if the conditions are met

## Boolean

### Description

Boolean allows you to create True / False conditions. Ask you a question, set conditions and the value will be set to True on the user if the conditions are met, otherwise it will be set to False.

### Popular use cases

* Has the user seen the campaign '10% discount'? True / False
* Has the user added an item in the cart over the last 2 days? True / False
* Has the user opened the last email sent? True / False

### How it works

1\. Name your new attribute

2\. Define the conditions you want to use.
