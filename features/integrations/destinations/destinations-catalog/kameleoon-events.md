# Kameleoon (events)

Kameleoon is an AI personalization and A/B testing SaaS platform for product managers and marketing teams who want to personalize the customer journey to maximize engagement, conversion and online revenue. Using this destination you can implement Kameleoon [TrackConversion API](https://customers.kameleoon.com/apisdk/doc/#/TrackConversion/get\_apisdk\_trackConversion) which can be used, after triggering an experiment, to measure performance characteristics according to the goals that make sense for your business.

## Key features

The Kameleoon (events) destination provides the following key features:

* **Events structure**: our [Event reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model fits [Kameleoon's Goal ID configuration](https://help.kameleoon.com/manage-goals/), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.

## Destination setup

### Configuration

| Settings                 | Description                                                                                                                                                                                                                                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Site Code                | <p><em><strong><code>Required</code></strong></em></p><p>Your <mark style="color:blue;">Site Code</mark> as provided by Kameleoon.</p>                                                                                                                                                         |
| Visitor Cookie Name      | <p><em><strong><code>Required</code></strong></em></p><p>Cookie name holding the visitor code. This can be set using the <mark style="color:blue;">Kameleoon (Builder)</mark> template which is available in our library following these steps: INTEGRATION ➜ Sources➜ Web Containers.</p>     |
| Commanders Act EventName | <p><em><strong><code>Required</code></strong></em></p><p>Map your Commanders Act events by adding their <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference">related names</a>. They need to match valid Kameleoon Goal Ids. <strong>[*]</strong></p> |
| Kameleoon GoalId         | <p><em><strong><code>Required</code></strong></em><br><em><strong><code></code></strong></em>Map your Kameleoon Goal Ids by adding their <a href="https://help.kameleoon.com/manage-goals/">related identifiers</a>. They need to match valid Commanders Act events.</p>                       |

{% hint style="info" %}
**\[\*]** Only these events will be bridged to Kameleoon.
{% endhint %}

## Field Mappings

| Commanders Act Properties | Kameleoon Properties |
| ------------------------- | -------------------- |
| `Site Code`               | `siteCode`           |
| `Visitor Cookie Name`     | `userID` **\[1]**    |
| `Kameleoon GoalId`        | `goalID`             |
| `properties.revenue`      | `revenue` **\[2]**   |

{% hint style="info" %}
**\[1]** The cookie content is set as value for the parameter`userID`.\
**\[2]** This is set for Commanders Act<mark style="color:blue;">`purchase`</mark>and<mark style="color:blue;">`refund`</mark>events only.
{% endhint %}

##
