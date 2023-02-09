# Events enrichment

Enrich incoming events in real-time before to send it to destinations.

Enrichment could come from the Product catalog, a Custom external API, Weather database (coming soon) or any Custom data store (coming soon).

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-02-09 à 17.21.55.png" alt=""><figcaption></figcaption></figure>

### Enrichment from Product catalog

You can import the full product catalog, as a result all details about products will be stored in our platform.

{% hint style="info" %}
Click [here](https://community.commandersact.com/platform-x/features/sources/sources-catalog/product-catalog) to learn how to import the product catalog
{% endhint %}

When you are collecting events with products properties, you can send only the `product_id`, and we will be able to enrich incoming events with more product properties coming from the stored product catalog (weight, materials, color...) and send it to the destination(s).

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-02-09 à 17.22.55.png" alt=""><figcaption></figcaption></figure>

#### Configuration

Select the event you want to enrich first.

Select the property that will be used as **matching key**, meaning how to do a link between the incoming event and the stored product catalog? Most of the time, the link will be the `product_id`. This property should be common between the one in the event and the one in the stored product catalog.

Select properties you want to add in the incoming event from the product catalog.

#### Advanced section

You can define here where properties coming from the product catalog will be added in incoming events (in the payload). By default, it is at the same level as the matching key. It could also be at the root of the event or custom (enter the position).



### Enrichment from Custom external API

Enrich events with data coming from any API.

For example, enrich a purchase event by adding properties from an external database. Via API, send a request with the matching key (an ID for example) and the API returns the desired data which will be integrated then into the purchase event.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-02-09 à 17.23.34.png" alt=""><figcaption></figcaption></figure>

#### Configuration

Select to which sources and events the enrichment will be applied.

Configure the API (Method, URL, Body, Header)

Select which properties from the API do you want to integrate into selected events.



### Enrichment from Weather database API

{% hint style="info" %}
Coming soon
{% endhint %}

You can currently manage it manually via [Enrichment from external API](events-enrichment.md#enrichment-from-custom-external-api), but a plug\&play version is in progress.

### Enrichment from Custom Data Store

{% hint style="info" %}
Coming soon
{% endhint %}
