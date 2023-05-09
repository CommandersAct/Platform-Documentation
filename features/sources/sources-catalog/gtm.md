---
description: Bridge your events in a seamless way.
---

# Google Tag Manager (GTM)

Commanders Act provides a GTM template to connect your existing GTM implementation to our serverside endpoint, in a secured environment.

## Setup

Summarizing all recommended steps:

1. Create a GTM source in Commanders Act
2. Add our template to your GTM implementation
3. Configure your tag

## Create a source in Commanders Act

In your Commanders Act dashboard:

* In the left pane menu, click on **Sources** > **Overview**.
* Click on the **Add source** button.
* In the catalog, search for the **Google Tag Manager** source and click on it.
* Click on **Configure** and set its name, environment and bound destinations.
* Once you're done, click on the **Create** button at the bottom.
* The source key will then be displayed:

![](../../../.gitbook/assets/serverside\_events\_bridge-key.png)

* Copy its value and keep it for later!

{% hint style="info" %}
**Hint**: If you have already created a GTM source, you can retrieve its key by browsing to its **Settings** tab.
{% endhint %}

## Add our template to GTM

First, access [GTM](https://tagmanager.google.com/) and then add our template "**Commanders Act | Serverside events bridge**" from the Google "[Community Template Gallery](https://tagmanager.google.com/gallery/#/owners/TagCommander/templates/Serverside-events-bridge)" in your workspace, then select `(1)` "**Tags**".

![](../../../.gitbook/assets/serverside\_events\_bridge1.png)

Click on `(2)` the "**New**" button.

![](../../../.gitbook/assets/serverside\_events\_bridge2.png)

Click on `(3)` the "**Tag Configuration**" area.

![](../../../.gitbook/assets/serverside\_events\_bridge3.png)

Click `(4)` the **magnifying glass** in the upper right corner.

![](../../../.gitbook/assets/serverside\_events\_bridge4.png)

Search for `(5)` the "**Commanders Act | Serverside events bridge**" custom template and click on it to start the configuration.

![](../../../.gitbook/assets/serverside\_events\_bridge5.png)

## Configure your tag

Start by filling `(6)` **a name for your tag** in the upper left corner.

![](../../../.gitbook/assets/serverside\_events\_bridge6.png)

{% hint style="success" %}
**Hint**: you may want to name your tag adding the event name you're going to implement in the end. (E.g. "_Commanders Act |_ Serverside events bridge _- **Purchase**_")
{% endhint %}

Input your `(7)` "**Commanders Act Site ID**" and `(8)` "**Commanders Act Source Key**" (refer to the first section on how to create a source and retrieve its key).

Select `(9)` the "**Commanders Act Event**" from the drop-down menu, which is the event you want to forward.

<figure><img src="../../../.gitbook/assets/serverside_events_bridge7 (1).png" alt="" width="536"><figcaption></figcaption></figure>

Depending on which event you select more (or less) fields will be presented. In case you don't input a mandatory field the template will highlight the missing entry so you can provide a proper mapping.

The "**Event Fields**" section contains fields that define the event itself and are mostly mandatory or highly recommended.

Events including the "**Product Fields**" section require [an array structure for your product information](https://community.commandersact.com/tagcommander/tips-and-tricks/best-practices/common-datalayer-variables#product-arrays). The first field will always be the `(10)` **base array** where the information is stored and all subsequent fields are the related properties - E.g. you can map the information about `(11)` the "**Product Id**" by filling the property name.

<figure><img src="../../../.gitbook/assets/serverside_events_bridge8 (1).png" alt=""><figcaption></figcaption></figure>

In the "**User Fields**" section you can set `(12)` the "**User Id**" and `(13)` "**User Email**" - Either one of them is required if you select the "Purchase" event. The `(14)` "**User Consent Categories**" is a mandatory field holding an array with the user's consent category identifiers.

<figure><img src="../../../.gitbook/assets/serverside_events_bridge9 (1).png" alt=""><figcaption></figcaption></figure>

It's important to define and map all category identifiers with their respective names. For example, you may have the following array: _\[1,2,4]_ and you defined the following relationship:

* 1 **➜** Advertising category
* 2 **➜** Analytics category
* 4 **➜** Functionality category

You also share with Commanders Act that the "Advertising category" must be enabled to activate the "Facebook CAPI." In this example, since the category identifier \[1] is included in the array we can activate the bridge and forward the event to Facebook.

{% hint style="info" %}
Ensure your category relationships are shared with Commanders Act.
{% endhint %}

{% hint style="warning" %}
Only with the agreed consent settings, we're allowed to bridge both the "Purchase" and "Refund" events to the "Facebook CAPI".
{% endhint %}

Complete your configuration by selecting the proper activation in the "Triggering" area / "Firing Triggers".

If you plan to setup [Facebook Conversion API](../../destinations/destinations-catalog/facebook/facebook-conversions-api.md) through your GTM source, follow this extra step to update your Facebook Pixel tag:

{% content-ref url="../../destinations/destinations-catalog/facebook/facebook-conversions-api/facebook-capi-through-gtm.md" %}
[facebook-capi-through-gtm.md](../../destinations/destinations-catalog/facebook/facebook-conversions-api/facebook-capi-through-gtm.md)
{% endcontent-ref %}
