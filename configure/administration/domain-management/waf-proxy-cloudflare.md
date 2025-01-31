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
   [https://](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer_3\&user_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[waf.myshop.com](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer_3\&user_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[/mix/v3/?firsttime=1\&tcs=5039\&chn=ref](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer_3\&user_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[errer\&src=referrer\_3\&user\_id=96177\&TCID=96177\&cmp=Promotion](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer_3\&user_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)[nal+game\&cty=Italy](https://waf.commandersact.com/mix/v3/?firsttime=1\&tcs=5039\&chn=referrer\&src=referrer_3\&user_id=96177\&TCID=96177\&cmp=Promotionnal+game\&cty=Italy)

## ​Troubleshooting

`Host` must be identified as [waf.commandersact.com](http://waf.commandersact.com/) which is what is expected.&#x20;

If the `host` is identified as [ca-trk-proxy.commander1.com](http://ca-trk-proxy.commander1.com/) which is not what is expected. This probably means that the proxy is setting the `host` parameter in the header to the domain in [commander1.com](http://commander1.com/) instead of leaving the original domain.

#### Expected proxy configuration

Here is the expected configuration of the proxy:

Haproxy :

```
listen tcp-443
  bind *:443
  mode tcp

  option log-health-checks
  option tcp-check

  server ca-trk-proxy ca-trk-proxy.commander1.com:443 resolvers dns check inter 30s check-sni ca-trk-proxy.commander1.com sni ssl_fc_sni check-ssl verify none
```

1. **server ca-trk-proxy**:
   * `server` is the keyword indicating the definition of a server in a backend section.
   * `ca-trk-proxy` is the name assigned to this server. It is used to identify the server in logs and stats.
2. [**ca-trk-proxy.commander1.com:443**](http://ca-trk-proxy.commander1.com:443/):
   * This specifies the address and port of the server. Here, the server is located at `ca-trk-proxy.commander1.com` and listens on port `443` (which is typically used for HTTPS).
3. **resolvers dns**:
   * `resolvers` specifies the DNS resolver section to use for resolving the server's hostname.
   * `dns` refers to a previously defined resolver section in the configuration that contains the DNS server details.
4. **check**:
   * This enables health checks for the server. HAProxy will periodically check if the server is up and running.
5. **inter 30s**:
   * This sets the interval between health checks to 30 seconds.
6. **check-sni** [**ca-trk-proxy.commander1.com**](http://ca-trk-proxy.commander1.com/):
   * `check-sni` specifies the Server Name Indication (SNI) to use during the health check. SNI is an extension of the TLS protocol that allows the client to specify the hostname it is trying to connect to at the start of the handshake process.
   * `ca-trk-proxy.commander1.com` is the hostname used for the SNI during the health check.
7. **sni ssl\_fc\_sni**:
   * `sni` specifies the SNI to use when establishing connections to the server.
   * `ssl_fc_sni` is a dynamic keyword that uses the SNI value from the frontend connection for this backend connection.
8. **check-ssl**:
   * This enables SSL checks during health checks, ensuring the SSL/TLS layer is properly established and validated.
9. **verify none**:
   * This option disables the verification of the server's SSL certificate during health checks. It means HAProxy will not validate the certificate against a certificate authority (CA).

In summary, this configuration line defines a backend server named `ca-trk-proxy` located at `ca-trk-proxy.commander1.com:443`. It uses the `dns` resolver for DNS resolution, performs health checks every 30 seconds, uses SNI during the checks, and does not verify the SSL certificate of the server during health checks.

