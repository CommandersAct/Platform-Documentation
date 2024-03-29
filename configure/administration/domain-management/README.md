# Domain Management

Improve the way you collect data with Commanders Act by using a first party approach.

The Domain Management Interface is the key to optimize your data collection configuration.

## What is a first-party cookie?

* **First-party cookies** are stored by the domain (website) you are visiting directly. They allow website owners to collect analytics data, remember language settings, and perform other useful functions that help provide a good user experience.
* **Third-party cookies** are created by domains other than the one you are visiting directly, hence the name third-party. They are used for cross-site tracking, rettargeting and ad-serving.

Until now all the data collected on a website was done mainly by tags, 3rd party tags, because the data is pushed to external servers (not owned by the brand but by some partners).

**Major browsers, such as Safari or Google Chrome**, decided to not allow anymore 3rd party cookies. That means **they will block cookies not coming from the brand itself but coming from partners** (such as Commanders Act). **They will detect all data flux pushed to a domain not related to the brand (3rd party domains).**

As a result, the workaround to continue to track and push data from websites to partners, is to use a domain owned by the brand, a first party domain. And the cookies should be set by this domain, this is what is called ‘1st party cookie’ because it seems to be generated by the brand itself and not from partners.

**There is a technical setup to do to initialize this 1st party tracking (on the domain level first and then on the cookie level).**

## What setup has to be done?

5 methods are possible:

* [WAF proxy](waf-proxy-cloudflare.md): easy to setup if you have a WAF like CloudFlare. The recommended method
* [CNAME record](cname-record.md) combined with [cookie CAID](cookie-caid.md):  still useful for Adblockers
* [A record](a-record.md)  combined with [cookie CAID](cookie-caid.md): not the best solution anymore, but still useful for Adblockers
* [On-premise Proxy](on-premise-proxy.md): more technical but preferred by some IT team. As efficient as WAF proxy.
* [CNAME record](cname-record.md) or [A record](a-record.md) without setting [cookie CAID](cookie-caid.md):  not recommended but still useful for Adblockers.

{% hint style="info" %}
Migration from 3rd party to 1st can be handled with Commanders Act consultants.
{% endhint %}
