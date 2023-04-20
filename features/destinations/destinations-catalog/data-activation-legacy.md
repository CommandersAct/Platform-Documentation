---
description: Only for advanced users
---

# Data Activation Legacy

{% hint style="info" %}
This destination is temporary, it is the first step of the migration to support events format in Data Activation module
{% endhint %}

Map events collected to Data Activation format (previously called Data Commander format). The goal is to collect events and map it to Data Activation format to be able to use the segmentation, audience connectors, augmented user attributes...

Select Data Activation Legacy on the destination catalog.

On the settings page, you can find the mapping:

## **Step 1: Data Activation Variable ← Event property mapping**

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-20 à 11.31.01.png" alt=""><figcaption></figcaption></figure>

Select on the left a Data Activation variable (user\_email ; user\_id...) and map it to the corresponding event's property (user.email ; value...).

You can use a static value, please enter it between quotation marks “ “.

## Step 2: **Data Activation page type (env\_template variable) ← Event name mapping**

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-20 à 11.31.19.png" alt=""><figcaption></figcaption></figure>

This mapping is dedicated for env\_template variable.&#x20;

On the left, enter the env\_template variable corresponding to the page type and map it to the event name (ex: funnel\_confirmation ⇒ purchase).

## Step 3: additional mapping, ONLY for page\_view event

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-20 à 11.31.29.png" alt=""><figcaption></figcaption></figure>

Only for page view event, map the env\_template variable corresponding to the page type to the page type in page view event (ex: productpage ⇒ product).

## Step 4: Advanced options

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-20 à 11.31.43.png" alt=""><figcaption></figcaption></figure>

If you check the box, purchase events will be stored on Data activation conversion storage.

For items mapping, you can choose to not check the box, as a result items will be stored as sent on purchase events.

If you check the box, you can define the mapping between product variables and items properties in event.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-20 à 16.22.41.png" alt=""><figcaption></figcaption></figure>

First, select the variable corresponding to the product list. Then, map the product variable to the item property in the event.
