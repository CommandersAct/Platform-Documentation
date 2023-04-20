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

You can use a static value, please enter them between quotation marks “ “.
