# Credit Usage

### What is the Credit Usage interface?

The **Credit Usage** interface helps you understand how your data consumption is calculated across your billing account.

It provides a **global view of all usage**, including all sites linked to the same billing account.

> 💡 You don’t need access to every site to see overall consumption.

***

### Why it matters

Your usage directly impacts your billing.\
This interface allows you to:

* Monitor how credits are consumed
* Identify the most consuming features
* Optimize your setup to reduce unnecessary usage

***

### Roles & Access

* Only **Account Managers** can view the Credit Usage UI
* They can grant this role to other users who are **Administrators on the same site**

***

### How to read the metrics

Each metric is based on two main dimensions:

* **Collection** → when data is received or processed
* **Storage** → when data is stored over time

> 💡 In simple terms:
>
> * _Collection = data entering the platform_
> * _Storage = data kept in the platform_

***

### TMS Client Side

| Metric                                  | Type               | Description                            |
| --------------------------------------- | ------------------ | -------------------------------------- |
| Client Side Container Call - Collection | Events             | Deduplicated web container calls       |
| Tagperformance - Collection             | Events             | Based on page views (sampling: 1/1000) |
| Tagperformance - Storage                | Storage            | Based on page views (sampling: 1/1000) |
| Deduplication - Collection & Storage    | Collection Storage | TMS deduplication (MySQL reporting)    |

***

### TMS Server Side

| Metric                        | Type    | Description                                        |
| ----------------------------- | ------- | -------------------------------------------------- |
| Server Side V1 - Collection   | Events  | All input events (deprecated)                      |
| Server Side V2 - Collection   | Events  | All input events (valid & invalid)                 |
| Server Side V2 - Output       | Events  | All output events                                  |
| Server Side V2 - Storage      | Storage | All events stored by Data Storage                  |
| Data Cleansing - Collection   | Events  | All events transformed with data Cleansing         |
| Event Enrichment - Collection | Events  | Number of processed events by Event Enrichment     |
| Destination log exporter      | Events  | All events collected by Destination "log exporter" |

***

### Consent

| Metric                               | Type   | Description                                                                  |
| ------------------------------------ | ------ | ---------------------------------------------------------------------------- |
| Privacy Banners - Collection         | Events | CMP banner views, deduplicated                                               |
| Cookie Scanner - Collection          | Events | Based on container calls (sampling: 1/100)                                   |
| Realtime Cookie Scanner - Collection | Events | Based on container calls: sampling tailored to your website's traffic volume |

***

### Customer Data

| Metric                                | Type        | Description                                      |
| ------------------------------------- | ----------- | ------------------------------------------------ |
| Activation - Collection               | Events      | Page views (Data Commander)                      |
| Activation - Storage                  | Storage     | Events stored per day (view, click, page\_view)  |
| Conversion - Storage                  | Storage     | Any conversion stored                            |
| Contacts - Storage                    | Storage     | Number of users created or updated               |
| Contact Imports - Collection & Update | Events      | Users updated per month                          |
| Contacts Enrichment - Processing      | Events      | User attribute enrichment                        |
| Custom Universe - Storage             | Storage     | Events stored per year                           |
| Segments - Processing                 | Pack Of 100 | Nb of Segments                                   |

***

### Campaign Analytics

| Metric                          | Type               | Description                               |
| ------------------------------- | ------------------ | ----------------------------------------- |
| Events - Collection             | Events             | Mix Page views                            |
| Events - Storage                | Storage            | Mix events Storage consumption            |
| Conversion - Collection         | Events             | Nb of conversions collected               |
| Conversion - Storage            | Storage            | All conversions stored (Mix orders)       |
| Tracking - Collection & Storage | Collection Storage | FREE of charge (not counted in invoicing) |

***

### Other

| Metric                    | Type   | Description                                    |
| ------------------------- | ------ | ---------------------------------------------- |
| API Platform - Collection | Events | Any API call (user API, geolocation API, etc…) |

## Best practices to optimize usage

> 💡 Here are a few practical tips:

* Avoid sending duplicate events, invalid events
* Limit unnecessary API calls
* Clean your data upstream when possible
