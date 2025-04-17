---
description: Only for Campaign Analysis Module (ex Mix Commander) customers
---

# Campaign Analysis Legacy

### Introduction

This destination allows you to collect events and map it for the module Campaign Analysis\
It can also turns events from Normalized Datalayer into touchpoints for Campaign Analysis module.

With this destination, you can use 4 standard events. \
To receive events in this destination, it requires as event name the 'Standard event name' described in the following array.\
\
Here's the list of Campaign Analytics touch points names vs Standard events names:

| Campaign Analysis touch point | Standard event name |
| ----------------------------- | ------------------- |
| impressions                   | ad\_view            |
| clicks                        | ad\_click           |
| sites                         | page\_view          |
| orders                        | purchase            |

If you need more information about these events, check the section [Events reference ](../../../developers/tracking/events-reference/)

### How to implement

#### 1/Select Campaign Analysis Legacy in the destination catalog.

<figure><img src="../../../.gitbook/assets/image (419).png" alt="" width="375"><figcaption></figcaption></figure>

#### 2/Choose your data source(s) 

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### 3/Name your destination and select an environment

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### 4/Setup your dimensions.

This destination will do an automatic mapping between the Campaign dimensions and the Standard properties.\
Here's the list of the automatic configuration done by this destination:

<table><thead><tr><th width="216">Campaign properties</th><th width="257.3333333333333">Standard dimensions</th><th>Campaign Dimension labels</th></tr></thead><tbody><tr><td>amount</td><td>value</td><td>Amount</td></tr><tr><td>cmp</td><td>campaign</td><td>Campaign</td></tr><tr><td>chn</td><td>medium</td><td>Channel from medium</td></tr><tr><td>cty</td><td>user.country</td><td>Country</td></tr><tr><td>currency</td><td>currency</td><td>Currency</td></tr><tr><td>dev</td><td>context.device.terminal_type</td><td>Device</td></tr><tr><td>e</td><td>user.email</td><td>E-mail</td></tr><tr><td>fmt</td><td>ad_format</td><td>Format</td></tr><tr><td>kw</td><td>keyword</td><td>Keyword, will be singular in NDL</td></tr><tr><td>med</td><td>medium</td><td>Medium</td></tr><tr><td>n_customer</td><td>user.is_new_customer</td><td>New Customer</td></tr><tr><td>orderid</td><td>id</td><td>Order id</td></tr><tr><td>os</td><td>status</td><td>Order Status</td></tr><tr><td>ot</td><td>type</td><td>Order Type</td></tr><tr><td>p</td><td>page_name</td><td>Page Name</td></tr><tr><td>pt</td><td>page_type</td><td>Page Type</td></tr><tr><td>ref</td><td>context.page.referrer</td><td>Referrer</td></tr><tr><td>src</td><td>source</td><td>Source</td></tr><tr><td>tclid</td><td>ad_cost_id</td><td>tclid</td></tr><tr><td>user_id</td><td>user.id</td><td>User id</td></tr></tbody></table>

If you use custom properties, or if you want to modify one or some of theses campaign dimensions with another property then the ones listed above, you will have to use the mapping table.

In all cases, a hand mapping is possible (between dimensions and properties). It will take the priority and override native mapping. Use the mapping table menu to make your own correspondence table:

<figure><img src="../../../.gitbook/assets/image (417).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you add a new custom dimension in your Campaign Analytics, you must to declare it manually also in this table of the destination's settings
{% endhint %}

If you do not want to use automatic mapping of dimensions with event properties, you can check the option "disable automatic configuration"

<figure><img src="../../../.gitbook/assets/image (415).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
This action will **block all** automatic mapping between Campaign dimensions and Standard properties
{% endhint %}

#### 5/Use the Properties Transformation menu (optional)

_Before to send your events to this destination you can, if needed, transform them to rename or remove some properties. Enter on the left the property name you want to add, delete or modify. Then enter on the right the property name where the value stands (or leave empty to remove the property)_

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### 6/Setup your filters - create your event(s) specification

You have to specify which event is concerned by this destination. Here's an example for a purchase (orders)&#x20;

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Don't forget to setup a consent filter to be RGPD compliant as well
{% endhint %}

#### 7/Your destination is ready to be activated!

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### 8/Go Further: modify timestamp

**ts\_override** property can be used to change the timestamp of an event

Example:

https://collect.commander1.com/events?tc\_s={site\_id\}}\&token={token}\&medium=seo\&source=google&<mark style="color:red;">**ts\_override=1716888588**</mark>\&event\_name=ad\_click\&campaign=sales\_2024\
