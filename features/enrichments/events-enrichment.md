# Events enrichment

Enrich incoming events in real-time before to send it to destinations.

Enrichment could come from the Product catalog, a Custom external API, Weather database (coming soon) or any Custom data store (coming soon).

<figure><img src="../../.gitbook/assets/Event enrichments.png" alt=""><figcaption></figcaption></figure>

Events enrichment allows collecting events, enriching it with stored data (coming from CRM, file imports…) and push it to destination(s).

For example, you are collecting events without email addresses. On a second hand, you are importing your CRM with email addresses. Based on the reconciliation key, we are able to enrich incoming events to add the email address and send it to the destination(s).

Other example, you are importing your product catalog with plenty of details about your products. When you are collecting events with products properties, you can send only the `product_id`, and we will be able to enrich incoming events with more product properties (weight, materials, color...) and send it to the destination(s).
