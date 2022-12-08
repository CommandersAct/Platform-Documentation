---
description: Transform/fix your events before to send them to destinations
---

# Data cleansing

Cleaning, fixing and preparing your data is crucial for success when using the Platform activation capabilities.\
The no-code approach allows you to create transformations using simple formula based on basic [functions ](supported-transformation-functions.md)and operators.

<figure><img src="../../../.gitbook/assets/image (1) (7).png" alt=""><figcaption></figcaption></figure>

You can choose between different kind of transformations:

* Rename event: simply change the name of an incoming event
* Derive event: create a new event from an existing one <mark style="color:blue;background-color:blue;">(c</mark><mark style="color:blue;background-color:blue;"><mark style="color:blue;">oming soon)<mark style="color:blue;"></mark>
* Modify properties: apply transformations and functions on properties
* Filter event: define rules to filter incoming events <mark style="color:blue;background-color:blue;">(c</mark><mark style="color:blue;background-color:blue;"><mark style="color:blue;">oming soon)<mark style="color:blue;"></mark>
* Custom code: create your own transformations <mark style="color:blue;background-color:blue;">(c</mark><mark style="color:blue;background-color:blue;"><mark style="color:blue;">oming soon)<mark style="color:blue;"></mark>

## Rename event

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-08 à 11.25.19.png" alt=""><figcaption></figcaption></figure>

First, give a name to the transformation and add a description if needed.

Select on which sources the rename transformation will be applied.

Select which event should be renamed. It is also possible to add more conditions, like rename the page view event to product view, if 'page\_type' contains 'product'.

Last step, enter the new event name.

## Modify properties

First, give a name to the transformation and add a description if needed.

Select on which sources the transformation will be applied.

Define conditions on events and/or properties, the transformation will be applied only regarding these conditions.

Select properties to transform. You can:

* rename the property ('rename to' option)
  * Example: rename 'date\_of\_birth' to 'birthdate'
* map/link to an existing property ('map to' option)
  * Example: map property 'price' to 'revenue'
* delete a property ('delete' option)
* change the value ('set value to' option)



<figure><img src="../../../.gitbook/assets/Live Normalization [READY] (1).png" alt=""><figcaption></figcaption></figure>
