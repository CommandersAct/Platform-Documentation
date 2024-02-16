# Condensed platform concepts

## CAX Platform : Features and Functions

Commanders Act: Cookieless platform for first-party customer data collection, normalization, enrichment, and real-time transmission.

### Components:

* Source: Libraries/APIs collect user actions (events) from various platforms (websites, apps, POS).
* Event: User actions tracked from sources and sent to CAX.
* Destination: Tools/partners receiving the collected data in suitable format. Examples include GA4, Facebook CAPI, Google Enhanced Conversion.
* Data store: Commanders Act's BigData database for storing events and imported data. Enables event or user enrichment, user segmentation, and data analysis.
* Identity resolution
* Data Insights : Campaign analysis, Automatic Ads budget optimisation (Adloop), Customer analytics, Control group

### Data Integration:

* Real-time tracking: Via OneTag, Javascript SDK, Google Tag Manager, Mobile SDKs, Rest API.
* Third-party tools: Connectors catalog, destination builder, webhook.
* Imports: Regular automated file imports (csv) for CRM users, offline conversions, product catalog, custom storage universe.
* Data API: Specific data transmission via Data JSON APIs.

### Data Quality:

* Confidence: In-app reporting and daily email digests for invalid event action.
* Normalized Datalayer UI: Interface for data schema definition and validation rule creation (event specs).
* QA automation: Event specification writing for QA process automation and real-time alert definition.
* Data Cleansing UI : Live data transformation feature for quick data error response.
* Event Delivery UI: Quality check for data transmission and event delivery history view.
* Event Inspector UI: Source and destination inspectors for specific event analysis/QA/debug

## OneTag

1. Add OneTag from tag library in web container. Options: Builder (no code) and Custom (manual code).
2.  Setup tag. Use `cact('trigger')` to record user actions. Format: `cact('trigger', '<event_name>', {<event_data>}, [config], [callback]);`. Events have names, properties. Example:&#x20;

    ```
    cact('trigger','sign_up', {
      method: 'email', 
      user: {
          consent_categories: [1,3,4,6]
      }
    });
    ```
3. Event types: standard (recommended, predefined names, parameters) and custom (user-defined). Use standard properties in custom events.
4. User consent automatically included in all events with Commanders Act CMP. With other CMP, manually add `consent_categories` inside `user`.
5. Override default parameters (`collectionDomain`, `sourceKey`, `siteId`) if needed. Set globally for all events with `cact('config')`.
6. Check functionality with Event Inspector.
7. Setup first destination. Add in Commanders Act platform, configure, choose source, manage user consent, save, check.
8. Server-side consent management: event sent to destination only if match between user consent categories and destination consent category.
