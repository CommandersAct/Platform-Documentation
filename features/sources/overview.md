# Sources Overview

## What is a source ?

A source is an emitter of events, more information [here](../../getting-started/concepts/#source).

## Source list

In _Sources / Overview_, you will find the full list of sources already configured.

You can search a source by name and filter on environment (production, staging, ...), status (active or inactive) and per destination

You can easily edit a source by clicking its name or the pencil icon.

{% hint style="info" %}
**Web containers** are special client-side sources, when editing them you will be redirected to dedicated interfaces
{% endhint %}

![](<../../.gitbook/assets/image (1) (1) (2) (1).png>)

## Trend and data quality

The trend represents the evolution of number of events received on the last month.

The data quality indicator allows to quickly visualize the status of the source, if data are of good quality (<img src="../../.gitbook/assets/image (17) (1) (1).png" alt="" data-size="line">) or not (<img src="../../.gitbook/assets/image (14) (2) (1).png" alt="" data-size="line">) on the last hour.

The quality score of events is represented by a weather icon:

* <img src="../../.gitbook/assets/image (17) (1) (1).png" alt="" data-size="line">sunny if the percent of correct events is equal to 100%
* <img src="../../.gitbook/assets/image (15) (2) (1).png" alt="" data-size="line">cloudy between 95% and 99.99%
* <img src="../../.gitbook/assets/image (16) (1).png" alt="" data-size="line">rainy between 90 and 95%
* <img src="../../.gitbook/assets/image (14) (2) (1).png" alt="" data-size="line">stormy below 90%
