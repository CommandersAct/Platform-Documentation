---
description: aka CloudFlare proxy
---

# WAF Proxy (CloudFlare,...)

Setup a reverse proxy DNS on a WAF like CloudFlare is an easy and reliable way for tracking purposes using 1st party cookies.

Contact your account manager for more details.

## Setup

1\. In Cloudflare (or your WAF), declare the tracking domain to be used and point it to our infra (for ex. waf.myshop.com) and point it to the endpoint we've defined for the proxy:&#x20;

**`ca-trk-proxy.commander1.com`**

<figure><img src="../../../.gitbook/assets/thumbnail_image001 (3).png" alt=""><figcaption><p>Setup a reverse proxy to Commanders Act on CloudFlare</p></figcaption></figure>

2\. On the DNS side, point your tracking domain (ex. waf.myshop.com) to Cloudflare (the CNAME is provided by cloudflare).

<figure><img src="../../../.gitbook/assets/thumbnail_image001 (4).png" alt=""><figcaption><p>Create a CNAME entry on CloudFlare</p></figcaption></figure>

3/ Then, adjust your existing tracking to reflect your new tracking domain.\
\
For example on campaign tracking: [https://](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[waf.myshop.com](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[/mix/v3/?firsttime=1\&tcs=5039\&chn=ref](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[errer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotion](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[nal+game\&cty=Italy](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)​
