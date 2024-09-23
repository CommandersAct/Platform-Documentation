# Content Security Policy

To ensure seamless integration and optimal functionality of our tools, customers must configure their Content Security Policy (CSP) to allow access to specific domains. This documentation page provides a list of the required endpoints, enabling customers to whitelist the necessary domains and maintain secure, uninterrupted access to our services.

For further details about CSP, visit this site:\
[https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)

## TMS <a href="#tag" id="tag"></a>

### CSPs&#x20;

* **img-src** on domains \*[.tagcommander.com](https://tagcommander.com) and \*[.commander1.com](https://commander1.com/)
* **script-src** on domains \*[.tagcommander.com](https://tagcommander.com) and \*[.commander1.com](https://commander1.com)
* **connect-src** on domain \*.[commander1.com](http://commander1.com/)
* **frame-src** on domains \*.[tagcommander.com](http://tagcommander.com/)

### CDN Hosting

Files are hosted on [cdn.tagcommander.com](http://cdn.tagcommander.com/) and returns Javascript

This includes containers, Privacy, Cookies sync, MIX and DATA Javascripts

### Credit Usage

[https://manager.tagcommander.com/utils/hit.php](https://manager.tagcommander.com/utils/hit.php) , returns a pixel

### Deduplication conversion collection

[https://manager.tagcommander.com/dedup/report/](https://manager.tagcommander.com/dedup/report/) , returns a pixel

### Deduplication customer journey set and get

https://\*[.commander1.com/dg3/ ](https://commander1.com/), returns Javascript

https://\*.[commander1.com/dc3/](https://commander1.com/) , returns a pixel

### Serverside Tracking v2

[https://collect.commander1.com/events](https://collect.commander1.com/events) , returns a pixel\
\
Serverside Datasave

[https://manager.tagcommander.com/datasave/](https://manager.tagcommander.com/datasave/) , returns a pixel

### Reach data collection

[https://engage.commander1.com/reach](https://engage.commander1.com/reach) , returns a pixel

### Cookies Sync

CDN javascript hosting

[https://sync.commander1.com ](https://sync.commander1.com/), returns a pixel

### TagPerformance data collection

CDN javascript hosting

[https://engage.commander1.com/tagsperf](https://engage.commander1.com/tagsperf), returns a pixel

### Serverside Tracking v1 (deprecated)

[https://serversideXXX.tagcommander.com/](https://tagcommander.atlassian.net/wiki/spaces/PS/pages/508002341/PLATFORM+-+CSP+Content+Security+Policy) , returns a pixel

[https://serversideXXX.commander1.com/](https://serversidexxx.commander1.com/) , returns a pixel

Notice : in debug mode (tc\_debug=1) returns some plain text ... not sure it's necessary to be mentionned as it should never be used in production

## CMP <a href="#trust" id="trust"></a>

### CSPs

* **img-src** on domains \*.[tagcommander.com](http://tagcommander.com/) and \*.[commander1.com](http://commander1.com/) and \*[.trustcommander.net](https://www.trustcommander.net/)
* **script-src** on domains cdn.[tagcommander.com](http://tagcommander.com/) and [cdn.trustcommander.net](https://cdn.trustcommander.net/)
* **frame-src** on [cdn.tagcommander.com](http://cdn.tagcommander.com/) and [cdn.trustcommander.net](https://cdn.trustcommander.net/)
* **connect-src** on domain \*[.commander1.com](https://commander1.com/) and \*[.trustcommander.net](https://www.trustcommander.net/)

### Cookie scanner

* collection URL : [//privacy.commander1.com/ctrust](https://privacy.commander1.com/ctrust)

### Privacy consent collection

CDN javascript hosting

[https://cdn.trustcommander.net](https://cdn.trustcommander.net/) (since may 2020)

[https://manager.tagcommander.com/utils/privacyHit.php](https://manager.tagcommander.com/utils/privacyHit.php) , returns a pixel

[https://manager.commander1.com/privacyHit.php](https://manager.commander1.com/privacyHit.php) , returns a pixel

[https://privacy.commander1.com/privacy-consent/ ,](https://privacy.commander1.com/privacy-consent/,) returns a pixel

[https://privacy.trustcommander.net/privacy-consent/ ,](https://privacy.commander1.com/privacy-consent/,) returns a pixel

## Campaign Analytics <a href="#mix" id="mix"></a>

### CSPs&#x20;

* **img-src** on domains \*.[commander1.com](https://commander1.com/)
* **script-src** on domains \*[.tagcommander.com](http://tagcommander.com/)

### Offsite data collection

https://\*.[commander1.com](https://commander1.com)/v3 , returns a pixel

https://\*.[commander1.com/](http://commander1.com/v3)c3 , returns a pixel

https://\*.[commander1.com/](http://commander1.com/v3)w3 , returns a pixel

### Onsite data collection

CDN javascript hosting

https://\*[.commander1.com/s3](https://commander1.com/) , returns a pixel

https://\*[.commander1.com/cs3](https://commander1.com/) , returns a pixel

https://\*[.commander1.com/o3](https://commander1.com/)[ ](https://commander1.com/), returns a pixel



{% hint style="info" %}
Examples

**Tracking type:** First

\
**Format URL:** `https://<customer_domain>/mix/cs3/?<parameters>`

\
**Full example:** `https://clientdomain.com/mix/cs3/?tcs=1234&rand=0.21688868283799656&chn=SEO&src=google&site=AlvieroMartini&cty=it&dev=d&ref=https://www.google.com/`\


***

\
**Tracking type:** Third

\
**Format URL:** `https://<customer_domain>/cs3/?<parameters>`

\
**Full example:** `https://customer.commander1.com/cs3/?tcs=1234&chn=SEO&src=google&cty=it&dev=d`\


_Note : the difference is the_ `/mix/` _in the URL for the first party tracking._
{% endhint %}

## Enrichment & Segmentation <a href="#data" id="data"></a>

### CSPs&#x20;

* **img-src** on domains \*[.commander1.com](https://commander1.com/)
* **script-src** on domains \*.[tagcommander.com](http://tagcommander.com/)
* **connect-src** on domain \*.[commander1.com](http://commander1.com/)

Onsite data collection

CDN javascript hosting

[https://engage.commander1.com/](https://engage.commander1.com/tagsperf)dms, returns a pixel

\
