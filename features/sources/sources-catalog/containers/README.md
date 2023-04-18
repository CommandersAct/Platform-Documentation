---
description: The container associated with a Tag Manager account.
---

# Web container

A web container is the browser-side component of _Commanders Act_ Enterprise Tag Management system.\
It is composed of a set of browser-side tags, rules, triggers and enriched web data layer. It is represented by a container javascript file that is put on each pages of your website.\
For information about how users setup and maintain containers, see the [dedicated Web container guide](https://community.commandersact.com/web-container/).

## Connect serverside destinations to a web container <a href="#onetag" id="onetag"></a>

Sending data from your web container to serverside destinations offers a lot of advantages (web performance, security, data accuracy/quality, etc.)

To start sending data, there is only one easy step to follow : adding the _Commanders Act_ **One Tag**.

> The last tag that you will ever setup.

The _One Tag_ allows you to send all your events to the Commanders Act platform in a normalized way, and once and for all, to benefit from all the serverside advantages that offer the platform.

## Recommandations for setup

In order to take advantage of all the benefits offered by a Web container, it is essential to [implement a datalayer](setup-guides-for-developers/datalayer-setup.md) on every page of your website.

Moreover, the [implementation of events](setup-guides-for-developers/browser-side-events-setup.md) on your site will allow you to obtain a more powerful and better quality tracking

{% hint style="info" %}
Please note : the following section concerns standard html implementation.\
If you're using a specific technology, don't hesitate to refer to our dedicated githubs to obtain our wrappers&#x20;

[Angular](https://github.com/CommandersAct/angular-tag-commander)

[Vue js](https://github.com/CommandersAct/vue-tag-commander)

[React](https://github.com/CommandersAct/react-tag-commander)

[Ngx](https://github.com/CommandersAct/ngx-tag-commander)
{% endhint %}

## Extensions

It is possible to extend Commanders Act TMS with additional modules:

| Module             | Description                                                        | Type        |
| ------------------ | ------------------------------------------------------------------ | ----------- |
| **TagPerformance** | A tool to measure onsite performance of Tags.                      | Client-Side |
| **Deduplication**  | A tool to selectively attribute conversions to marketing channels. | Client-Side |
| **TagFirewall**    | A tool to black- or whitelist Tags.                                | Client-Side |

{% hint style="info" %}
These modules are set up and configured by a Commanders Act consultant.
{% endhint %}
