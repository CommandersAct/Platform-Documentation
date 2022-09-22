# Concepts

Basically, the platform libraries/API ([Source](concepts.md#source)) collects user actions ([Event](concepts.md#event)) on your website/app/etc.\
These events are sent to the platform servers and are then enriched, normalized and translated in each tool ([Destination](concepts.md#destinations)) format, so that they can be sent to your chosen destinations.

Platform servers can also store events, users and custom data in the Commanders Act database ([Data store](concepts.md#data-store)) and send this data to your storage system (by FTP, email, ...), BI system, etc.

## Event

An event represents an action made by a user on your website or application. To track that action, you send an event that contains the data and will be received by Commanders Act.\
[More information here](../../developers/tracking/about-events/).

## Source

A source is an emitter of events. It can represents your website, your mobile app, a point of sale (POS) etc. Defining your sources allow you to easily manage and monitor where your events are coming from.\
See our [source catalog here](sources/sources-catalog/).

## Destination

Destinations are the partners where you eventually want the collected data to go. Commanders Act provide a library of many destinations ready to be used, like Facebook CAPI or Google enhance Conversion.\
See our [destination catalog here](destinations/destinations-catalog/).

## Data store

Data store is the name of Commanders Act BigData database. You can store here your events and your [imported data](../../getting-started/integrating-your-data.md#imports) (product catalog, etc.)\
Storing data inside the Data store allows you then to [enrich ](../enrichments/)your events by retrieving additional data in any storage universe. It also allows you to create user [segments](../customers/segment/).
