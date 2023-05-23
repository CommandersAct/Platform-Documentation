# Integrating your data

There are several ways how to get your data into Commanders Act platform.

## Real-time Commanders Act tracking

|                            |                                                                                                                                                                            |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Web container (OneTag)** | You can use the [OneTag](integrating-your-data/onetag-tutorial.md) to send events via our tag manager system.                                                              |
| **Javascript SDK**         | You can use the [Javascript SDK](../features/sources/sources-catalog/web/js-sdk/) to track events directly from your website code/CMS/TMS.                                 |
| **Google Tag Manager**     | If you are using GTM client-side container, you can use our serverside platform by using the [Commanders Act GTM template](../features/sources/sources-catalog/web/gtm.md) |
| **Mobile SDKs**            | The [Mobile SDKs](../features/sources/sources-catalog/mobile-app.md) are the best way to simplify tracking in your iOS/Android apps.                                       |
| **Rest API**               | If you need to build your custom solution, have a look to the [http tracking API](../features/sources/sources-catalog/server/http-tracking-api/).                          |

## Third party tools

Commanders Act also offers connectors to third party tools, visit the [source catalog](../features/sources/sources-catalog/) to explore the full list.

## Imports

It is possible to import data to Commanders Act through regular automated file imports (csv), such as:

* [CRM users](../features/sources/sources-catalog/import-crm-users/users-file-importer.md)
* [Conversions](../features/sources/sources-catalog/import-conversions/conversions-files-importer.md) and [Product catalog](../features/sources/sources-catalog/product-catalog/)
* Custom storage universe

## Data API

You can send your specific data through our [Data JSON APIs](../developers/tracking/data-api/).
