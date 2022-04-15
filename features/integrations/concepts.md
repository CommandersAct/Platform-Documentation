# Concepts

Basically, the platform libraries/API ([Source](concepts.md#source)) collects user actions ([Event](concepts.md#event)) on your website/app/etc.\
These events are sent to the platform servers and are then enriched, normalized and translated in each tool ([Destination](concepts.md#destinations)) format, so that they can be sent to your chosen destinations.

## Event

An event represents an action made by a user on your website or application. To track that action, you send an event that contains the data and will get received by Commanders Act.

## Source

A source is an emitter of events. It can represents your website, your mobile app, a point of sale (POS) etc. Defining your sources allow you to easily manage and monitor where your events are coming from.

## Destination

Destinations are the partners where you eventually want the collected data to go. Commanders Act provide a librrary of many destinations ready to be used, like Facebook CAPI or Google enhance API.

## Data store

Data store is the name of Commanders Act BigData database. You can store here your events and your imported data (product catalog, etc.)\
Storing data inside the Data store allows you then to enrich your events by retrieving additional data in any storage universe.
