---
description: aka CloudFlare proxy
---

# WAF Proxy (CloudFlare,...)

Setup a reverse proxy DNS on a WAF like CloudFlare is an easy and reliable way for tracking purposes using 1st party cookies.

Contact your account manager for more details.

## Setup

### Create your WAF

1\. In Cloudflare (or your WAF), declare the tracking domain to be used and point it to our infra (for ex. waf.myshop.com) and point it to the endpoint we've defined for the proxy:&#x20;

**`ca-trk-proxy.commander1.com`**

<figure><img src="../../../.gitbook/assets/thumbnail_image001 (3).png" alt=""><figcaption><p>Setup a reverse proxy to Commanders Act on CloudFlare</p></figcaption></figure>

2\. On the DNS side, point your tracking domain (ex. waf.myshop.com) to Cloudflare (the CNAME is provided by cloudflare).

<figure><img src="../../../.gitbook/assets/thumbnail_image001 (4).png" alt=""><figcaption><p>Create a CNAME entry on CloudFlare</p></figcaption></figure>

### Declare it in Domain Management

1. Declare the domain\
   Use our interface Domain Management to declare this domain and adjust the way Commanders Act collect the datas\
   `Administration > Domain Management`

<figure><img src="../../../.gitbook/assets/image (490).png" alt=""><figcaption></figcaption></figure>

2.  Activate the domain\
    Turn ON the option "Containers Integration" will allow the domain to be included in the container configuration.

    All Commanders Act tags will switch to first party collection.

    This action will affect Consent, Deduplication, Campaign, Segment, Server Side

<figure><img src="../../../.gitbook/assets/image (492).png" alt=""><figcaption></figcaption></figure>

**What happens when I have 2 or more domains?**

It prioritizes the domain of the website where the container is loaded. If no domain matches the domain of the website, the 1st in the list is used.

{% hint style="warning" %}
At this point, **WebContainers and Privacy banners** should be **regenerated and deployed.**
{% endhint %}

3. If applicable, adjust your existing tracking to reflect your new tracking domain.\
   \
   For example on a View Campaign tracking hit:\
   [https://](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[waf.myshop.com](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[/mix/v3/?firsttime=1\&tcs=5039\&chn=ref](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[errer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotion](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[nal+game\&cty=Italy](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)​
