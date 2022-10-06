# Personalized ads

## Use case description

🎯 Goal:

Create custom audiences to send to Facebook, Google, Criteo…

Depending on their behaviour (product view, email opened, add to cart…), CRM information or any actions your customers performed, create advanced segments and activate it on our partners’ ad network: Facebook, Google, Criteo…

Then create relevant and personalized ads for these users coming from your segments.

🔧 Complexity: 1/5

💰 ROI: Medium

![](<../../.gitbook/assets/persoads (1).png>)

## Use case setup

Step 1: create a segment, like for example with customers who saw your latest product but didn’t buy on the last 2 days (not online, not in shops)

Step 2: create a stream to push your segment to partners like Facebook, Google, Criteo…

Step 3: on our partners’ platform, create relevant and personalized ads and activate it for the audience previously sent to the partner you selected.

{% hint style="info" %}
**Quick Tip**:

Use our **Control Group feature** to measure results with the comparison of conversion uplift between the exposed population and the control group
{% endhint %}

## Exclude audience

**Stop exposing** a specific audience to a campaign.

Customers who just bought, lost customers… don’t expose them anymore and avoid spending too much money for customers who are not interested anymore. Moreover, manage the exposure capping.

For example, you want to target customers who saw a specific product but didn't buy. But you don't want to target users who just bought this specific product offline, in your shops. Simply create 2 segments, push them to the partner and use one for targeting and one for exclusion.
