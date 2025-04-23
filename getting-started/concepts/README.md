# How the platform works

Commanders Act is a cookieless platform that allows you to **collect, normalize/fix, enrich, check and send** in real time your first-party customer data.

<figure><img src="../../.gitbook/assets/image (12) (2).png" alt=""><figcaption></figcaption></figure>

Basically, the platform libraries/API ([Source](./#source)) collects user actions ([Event](./#event)) on your website/app/etc.\
These events are sent to the platform servers and are then (in this order) [fixed](../../features/data-quality/data-cleansing/), [normalized](../../features/data-quality/event-specification.md), [enriched](../../features/enrichments/), [checked](../../features/data-quality/), filtered and translated in each tool ([Destination](./#destinations)) format, so that they can be sent to your chosen destinations.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Platform servers can also store events, users and custom data in the Commanders Act database ([Data store](./#data-store)) and send this data to your storage system (by FTP, email, S3, ...), BI system, etc.\
The user storage is based on a realtime [identity resolution system](../../features/identity-resolution.md) that give you a cross-device single view of your users (profiles), allowing you to build segments and use audience-based destination.

## Event

An [event ](../../developers/tracking/about-events/)represents an action made by a user on your website or application. To track that action, you send an event that contains the data and will be received by Commanders Act.

## Source

A [source ](../../features/sources/)is an emitter of events. It can represents your website, your mobile app, a point of sale (POS) etc. Defining your sources allow you to easily manage and monitor where your events are coming from.\
See more on:

{% content-ref url="../integrating-your-data.md" %}
[integrating-your-data.md](../integrating-your-data.md)
{% endcontent-ref %}

{% content-ref url="../../features/sources/sources-catalog/" %}
[sources-catalog](../../features/sources/sources-catalog/)
{% endcontent-ref %}

## Destination

[Destinations ](../../features/destinations/)are the partners/tools where you eventually want the collected data to go. Commanders Act provide a library of many destinations ready to be used, like GA4, Facebook CAPI or Google Enhanced Conversion.\
See our [destination catalog here](../../features/destinations/destinations-catalog/).

## Data store

Data store is the name of Commanders Act BigData database. You can store here your events and your [imported data](../integrating-your-data.md#imports) (product catalog, etc.)\
Storing data inside the Data store allows you then to [enrich ](../../features/enrichments/events-enrichment.md)your events by retrieving additional data in any storage universe. It also allows you to create user [segments](../../features/customers/segment/) and to benefit from analysis and insights.

## Data layer

A data layer is a specification of your data for tracking customer interactions. This can include data from websites, mobile apps, connected devices, and offline sources. The data layer enables your third-party vendor solutions and serves as the basis for your data-focused initiatives.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}
