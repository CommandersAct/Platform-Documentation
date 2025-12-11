# Events enrichment

Enrich incoming events in real-time before to send it to destinations.

Enrichment could come from the Product catalog, a Custom external API, Weather database (coming soon) or any Custom data store.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-02-09 à 17.21.55.png" alt=""><figcaption></figcaption></figure>

## Enrichment from Product catalog

You can import the full product catalog, as a result all details about products will be stored in our platform.

{% hint style="info" %}
Click [here](https://community.commandersact.com/platform-x/features/sources/sources-catalog/product-catalog) to learn how to import the product catalog
{% endhint %}

When you are collecting events with products properties, you can send only the `product_id`, and we will be able to enrich incoming events with more product properties coming from the stored product catalog (weight, materials, color...) and send it to the destination(s).

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-02-09 à 17.22.55.png" alt=""><figcaption></figcaption></figure>

### Configuration

Select the event you want to enrich first.

Select the property that will be used as **matching key**, meaning how to do a link between the incoming event and the stored product catalog? Most of the time, the link will be the `product_id`. This property should be common between the one in the event and the one in the stored product catalog.

Select properties you want to add in the incoming event from the product catalog.

### Advanced section

You can define here where properties coming from the product catalog will be added in incoming events (in the payload). By default, it is at the same level as the matching key. It could also be at the root of the event or custom (enter the position).

## Enrichment from Custom external API

Enrich events with data coming from any API.

For example, enrich a purchase event by adding properties from an external database. Via API, send a request with the matching key (an ID for example) and the API returns the desired data which will be integrated then into the purchase event.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-02-09 à 17.23.34.png" alt=""><figcaption></figcaption></figure>

### Configuration

Select to which sources and events the enrichment will be applied.

Configure the API (Method, URL, Body, Header)

Select which properties from the API do you want to integrate into selected events.

## Enrichment from Weather database API

{% hint style="info" %}
Coming soon
{% endhint %}

You can currently manage it manually via [Enrichment from external API](events-enrichment.md#enrichment-from-custom-external-api), but a plug\&play version is in progress.

## Enrichment from Custom Data Store

Enrich events from previously stored events.\
It allows you to store selected event and properties and use them later to enrich events, providing a more complete set of data for your marketing and analysis needs.

### Key Features

#### Storage of Event

* **Selective Storage**: Choose specific properties of an event to store after the event is cleaned. This ensures only relevant and clean data is stored.
* **Storage Duration**: By default, properties are stored for 1 day.

#### Event Matching

* **Matching Key**: Define a **unique key** to match events over time. This key helps link related events, allowing the properties of past events to be used in future ones.

#### Event Enrichment

* **Property Injection**: Automatically inject properties from past stored events into more recent events. This creates a comprehensive dataset for each significant event in the customer journey.

### Use Case Example

Imagine that a customer adds a product to their cart, generating an `add_to_cart` event. A few hours later, the same customer completes the purchase, generating a `purchase` event. With the _Event Enrichment_ feature, you can enrich the `purchase` event in realtime with properties from the earlier `add_to_cart` event, before the event is sent to your destinations.

### How to Use the Enrichment Event Feature

#### Step 1: Create your Storage Settings

1. **Access Storage Settings**: Go to the Data Governance -> Storage settings.
2.  **Manage Storage Settings**: Click on "New Storage" to create a new Storage.\\

    <figure><img src="/broken/files/rlQvSbmZAc69jYz72f5Z" alt=""><figcaption></figcaption></figure>

To learn more about how to use this feature, and get tips about Storage Settings creation, please [read the dedicated page](storage-settings.md)\\

#### Step 2: Enrich Events

1.  **Create an enrichment**: In the Event Enrichment section, choose the option Custom Data Store\\

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
2.  **Define Enrichment**:

    * **Name**: Name your enrichment rule.
    * **Select Sources and Environment**
    * **Select the Storage Settings** you want to use for this enrichment
    *   **Choose Event**: Select the event you want to enrich.\\

        <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
    * **Select Properties**: Define which properties from the stored event should be injected into the new event. Select in "Storage Settings" column the properties, as it is in your Storage. Select the property you want to enrich in the "Event Property"\
      The storage do not replace or override the value of an existing property. The storage will create new properties.\
      If you want to override an existing value, click the option "override"
    * **Review Settings**: Ensure all settings are correctly configured.
    * **Save**: Save the new enrichment settings.\\

    <figure><img src="/broken/files/ZFMJsIsw0T0s3AjeRdzB" alt=""><figcaption></figcaption></figure>

* **Administrators Only**: This feature is accessible only to users with Administrator privileges. Custom profiles can be created to grant specific access to other users.

### Benefits

* **Complete Data Sets**: Enriching events ensures that all relevant data is available for analysis and marketing actions.
* **Enhanced Customer Insights**: Gain a more detailed understanding of customer behavior by linking related events over time.
