---
description: Container strategies for common setups.
---

# Common Container Strategies

A Container Strategy is the layout of the Web Container of a site. Following you will find recommended Container Strategies for common types of websites and businesses.

## Ecommerce

Ecommerce websites require a mix of personalization, analytics and conversion Tags. To optimise website performance it is recommended to use three Containers.

| Container        | Type     | Placement                  | Tags                            |
| ---------------- | -------- | -------------------------- | ------------------------------- |
| Head Container   | `<head>` | All pages                  | A/B-testing and personalization |
| Body Container   | `<body>` | All pages or catalog pages | Analytics and tracking          |
| Funnel Container | `<body>` | Funnel pages               | Conversion                      |

With this setup it is possible to avoid conversion Tag JavaScript snippets on catalog pages—this results in smaller Container file sizes and therefore quicker loading times for SEO relevant catalog pages.

## Publisher

Publisher websites primarily require analytics Tags. Therefore it is recommended to only use one Container.

| Container      | Type     | Placement                  | Tags                   |
| -------------- | -------- | -------------------------- | ---------------------- |
| Body Container | `<body>` | All pages or catalog pages | Analytics and tracking |

Using one `<body>` Container helps to have minimal impact on the page loading time, which is crucial for SEO of Content pages like news articles.&#x20;

In case A/B-testing and personalization Tags are used, the additional implementation of a `<head>` Container is recommended.
