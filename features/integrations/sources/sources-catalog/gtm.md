---
description: Bridge your events in a seamless way.
---

# GTM

Commanders Act provides a GTM template to connect your existing GTM implementation to our serverside endpoint, in a secured environment.

## Setup

Summarizing all recommended steps:

1. Add our template
2. Configure your tag

## Add our template

First, access [GTM ](https://tagmanager.google.com)and then add our template "**Commanders Act | Serverside events bridge**" from the Google "[Community Template Gallery](https://tagmanager.google.com/gallery/#/owners/TagCommander/templates/Serverside-events-bridge)" in your workspace, then select `(1)` "**Tags**".

![](../../../../.gitbook/assets/serverside\_events\_bridge1.png)

Click on `(2)` the "**New**" button.

![](../../../../.gitbook/assets/serverside\_events\_bridge2.png)

Click on `(3)` the "**Tag Configuration**" area.

![](../../../../.gitbook/assets/serverside\_events\_bridge3.png)

Click `(4)` the **magnifying glass** in the upper right corner.

![](../../../../.gitbook/assets/serverside\_events\_bridge4.png)

Search for `(5)` the "**Commanders Act | Serverside events bridge**" custom template and click on it to start the configuration.

![](../../../../.gitbook/assets/serverside\_events\_bridge5.png)

## Configure your tag

Start by filling `(6)` **a name for your tag** in the upper left corner.

![](../../../../.gitbook/assets/serverside\_events\_bridge6.png)

**Hint**: you may want to name your tag adding the event name you're going to implement in the end. (E.g. "_Commanders Act |_ Serverside events bridge _- **Purchase**_")&#x20;

Input your `(7)` "**Commanders Act Site ID**" and select `(8)` the "**Commanders Act Event**" from the drop-down menu, which is the event you want to forward.

![](../../../../.gitbook/assets/serverside\_events\_bridge7.png)

Depending on which event you select more (or less) fields will be presented. In case you don't input a mandatory field the template will highlight the missing entry so you can provide a proper mapping.

The "**Event Fields**" section contains fields that define the event itself and are mostly mandatory or highly recommended. &#x20;

Events including the "**Product Fields**" section require [an array structure for your product information](https://community.commandersact.com/tagcommander/tips-and-tricks/best-practices/common-datalayer-variables#product-arrays). The first field will always be the `(9)` **base array** where the information is stored and all subsequent fields are the related properties - E.g. you can map the information about `(10)` the "**Product Id**" by filling the property name.

![](../../../../.gitbook/assets/serverside\_events\_bridge8.png)

In the "**User Fields**" section you can set `(11)` the "**User Id**" and `(12)` "**User Email**" - Either one of them is required if you select the "Purchase" event. The `(13)` "**User Consent Categories**" is a mandatory field holding an array with the user's consent category identifiers.

![](../../../../.gitbook/assets/serverside\_events\_bridge9.png)

It's important to define and map all category identifiers with their respective names. For example, you may have the following array: _\[1,2,4]_ and you defined the following relationship:&#x20;

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

Complete your configuration by selecting the proper activation in the "Triggering" area / "Firing Triggers".\
