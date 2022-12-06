# Concepts

Basically, the platform libraries/API ([Source](./#source)) collects user actions ([Event](./#event)) on your website/app/etc.\
These events are sent to the platform servers and are then [checked](../../features/data-quality/), [enriched](../../features/enrichments/), [normalized ](../../features/data-quality/normalized-datalayer.md)and translated in each tool ([Destination](./#destinations)) format, so that they can be sent to your chosen destinations.

Platform servers can also store events, users and custom data in the Commanders Act database ([Data store](./#data-store)) and send this data to your storage system (by FTP, email, ...), BI system, etc.

## Event

An [event ](../../developers/tracking/about-events/)represents an action made by a user on your website or application. To track that action, you send an event that contains the data and will be received by Commanders Act.\
[More information here](../../developers/tracking/about-events/).

## Source

A [source ](../../features/sources/)is an emitter of events. It can represents your website, your mobile app, a point of sale (POS) etc. Defining your sources allow you to easily manage and monitor where your events are coming from.\
See our [source catalog here](../../features/sources/sources-catalog/).

## Destination

[Destinations ](../../features/destinations/)are the partners where you eventually want the collected data to go. Commanders Act provide a library of many destinations ready to be used, like Facebook CAPI or Google enhance Conversion.\
See our [destination catalog here](../../features/destinations/destinations-catalog/).

## Data store

Data store is the name of Commanders Act BigData database. You can store here your events and your [imported data](../integrating-your-data.md#imports) (product catalog, etc.)\
Storing data inside the Data store allows you then to [enrich ](../../features/enrichments/)your events by retrieving additional data in any storage universe. It also allows you to create user [segments](../../features/customers/segment/) and to benefins from analysis and insights.
