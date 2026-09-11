# Commanders Act Gateway

This document describes how to deploy **Commanders Act Gateway**, a **unified first-party gateway** that uses **one single setup and one single path on your domain** to power multiple tracking and hosting use cases.

Commanders Act Gateway includes **Google Tag Gateway**, but is **not limited to Google**.\
It is designed to serve and collect data for **all your marketing and analytics partners**, using the same first-party infrastructure.

One setup, one first-party path, three usages:

* Google Tag Gateway (GA4, Google Ads)
* First-party tracking to all server-side destinations
* First-party hosting of third-party libraries

If your goal is to implement Google Tag Gateway, you are in the right place.\
If your goal is to build a durable, vendor-agnostic first-party tracking architecture, you are also in the right place.

<figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-5c269a1cb309c24a7504446eef7a53b7aafd97d9%2Fschema_google_ads%20(4).png?alt=media" alt=""><figcaption></figcaption></figure>

***

## Why use Commanders Gateway?

### 1. Advantages of using a gateway

A gateway setup improves **data collection quality and completeness** across your marketing stack.

* Vendor scripts are served from your own domain, which redauces the likelihood of being blocked by adblockers.
* Browser restrictions (such as Safari’s ITP) often limit or block third-party cookies and some 1st party javascript cookies, but with a first-party server-side setup, measurement remains more reliable.
* This ensures **more accurate tracking**, providing partners with higher-quality signals for measurement, attribution, and optimization.

### 2. Advantages of using Commanders Gateway

On top of the benefits of any gateway approach, **Commanders Gateway** adds unique advantages:

* Not limited to Google Tag Gateway — the same durable setup applies to **all your partners** (Meta, Snapchat, Bing, Awin, etc.).
* Unified setup: a **single path** (`/mypath`) serves and proxies all vendor libraries.
* Obfuscated JavaScript filenames are automatically provided by Commanders Act, making detection by blocking lists far more difficult.
* With the same simple path, you can also activate other **first-party hosting and tracking features** such as: hosting your tag management containers, server-side event tracking, or anonymous CMP statistics. A single setup powers your whole first‑party hosting and tracking system.
* A centralized configuration simplifies deployment and maintenance while remaining **future-proof** against upcoming browser restrictions.

***

## Overview

**Commanders Gateway** lets you deploy marketing and measurement tags using your **own first-party infrastructure**, hosted on your website’s domain.\
This infrastructure sits between your website and your partners’ services (Google, Meta, Bing, Snapchat, Awin, etc.).

With Commanders Gateway:

* Google libraries (gtag.js / gtm.js) are loaded directly from your **first-party domain**.
* Other vendor libraries are served from `/mypath/js/` using **obfuscated filenames**.
* All measurement requests are proxied through your domain before being forwarded to the respective partner endpoints.

***

## Google Tag Gateway (GTG) and consent

{% hint style="info" %}
This section is written for the verification of requirements on Consent Mode with Google Tag Gateway (GTG). It explains what GTG changes for consent, how to check enrollment, and what to do if a "late" consent signal is detected on a GTG-enrolled domain.&#x20;
{% endhint %}

#### What Google Tag Gateway changes for consent

**Google Tag Gateway (GTG) for advertisers** lets a website serve Google tags (`gtag.js`, `gtm.js`) from the site's own first‑party domain instead of `googletagmanager.com`, using a CDN, load balancer, or web server. Commanders Act Gateway can be used to implement GTG (see [Architecture](commanders-tag-gateway.md#architecture) below).

GTG does not change _what_ consent mode does — it changes **where the Google tag is served from and, critically, when it can load relative to your consent banner**. That timing is where the impact on consent lives:

* **One‑click / automated CDN injection** (the in‑UI setup offered by Google for Cloudflare, Akamai, Fastly, or a Google Cloud Load Balancer) makes Google inject the routing rule directly into your CDN or load balancer configuration, generally placing the Google tag very early in the page. Because this injection happens **outside your tag management or page source**, you typically **can no longer control the order in which scripts load** relative to your consent banner. If your CMP's consent stub has not yet run and set default consent states, the Google tag can fire first.
* **Manual / self-service GTG setup**, where you configure the routing yourself and reference the first‑party script directly in your page source, keeps script load order under your control — you decide whether the Google tag or your CMP's consent script loads first.

When a Google tag fires before your CMP has set a default consent state, this is what Google calls a **"late" consent signal**: the tag runs with an unknown/undefined consent state instead of respecting the default your CMP intended to set. This can cause tags to behave as if no consent framework were present, and it is flagged by Google's own diagnostic tools (see [Verification](commanders-tag-gateway.md#verification-checklist) below).

{% hint style="warning" %}
Rolling back GTG is **not** the recommended way to resolve a late consent signal: doing so forfeits the first‑party measurement durability benefits GTG is designed to provide. The recommended remediation's are described in [If a late consent signal is detected](commanders-tag-gateway.md#if-a-late-consent-signal-is-detected-and-gtg-enrollment-is-confirmed) below.&#x20;
{% endhint %}

#### Google's documentation on GTG

* [Google tag gateway for advertisers – overview](https://developers.google.com/tag-platform/tag-manager/gateway)
* [Set up Google tag gateway for advertisers](https://developers.google.com/tag-platform/tag-manager/gateway/setup-guide)

#### Verify if a tag is enrolled in GTG

Before investigating a consent issue related to GTG, confirm whether the domain is actually enrolled. Any of the following methods can be used:

* **In the Google product UI** — In Google Tag Manager, go to **Admin → Google tag gateway**. Each domain is listed with a status: `First-party` (GTG is active), `Not started` (GTG has not been enabled), or `Activated domains` for domains configured manually or through a different tag. The same status is available from the equivalent screen in Google Ads and Google Analytics.
* **Google Tag Assistant** — Connect Tag Assistant to the website, trigger the relevant tags, and check where the Google tag's requests are actually served from and sent to (**Summary → Output → Hits Sent**). If Google tag requests are routed to your own domain (for example `example.com/mypath/` or `example.com/gtag/js`) instead of `www.googletagmanager.com` or `www.google-analytics.com`, GTG is active for that page.
* **Browser DevTools** — In the Network tab, check whether the script and measurement requests for `gtag.js` / `gtm.js` originate from your first‑party domain rather than a Google domain.

#### If a "late" consent signal is detected and CAGT enrollment is confirmed

A late consent signal typically shows up in Google's [consent debugging tools](https://developers.google.com/tag-platform/security/guides/consent-debugging) (Tag Assistant's consent timeline, or a console warning) as the Google tag firing before a default consent state was set, or a consent state reported as "unknown" at the moment the tag fired.

**Once you have confirmed both (a) a late consent signal, and (b) that GTG is enrolled on the domain**, Google recommends one of the following remediation paths:

1. **Adopt Advanced Consent Mode** in your Commanders Act CMP setup, and configure **Data Transmission Controls** and **Global Consent Defaults** in your Google tag settings (Google Ads, GA4, or Campaign Manager 360) according to your compliance needs. This is the mechanism Google recommends specifically for GTG‑enabled tags — see [why below](https://claude.ai/chat/4300c170-a117-4d9d-ae3c-86117d316787#why-advanced-consent-mode-u+c-is-recommended-for-gtg).
2. **Migrate all your Google tags into a single Google Tag Manager container, and deploy that container itself via GTG**, instead of injecting individual gtag.js tags. This centralizes load‑order control inside GTM, so GTM's built‑in consent checks apply to every Google tag in the container regardless of how the container script is routed.
3. **Set up GTG manually**, so that you — not an automated CDN injection — control where the first‑party GTG script reference is placed in your page source, relative to your Commanders Act consent banner script.

{% hint style="info" %}
These three options are not mutually exclusive. For example, a manual GTG setup (option 3) can be combined with Advanced Consent Mode (option 1) for additional resilience if load order is ever affected by a future page or CDN change.&#x20;
{% endhint %}

**Why Advanced Consent Mode is recommended for GTG**

Advanced Consent Mode is the mechanism Google recommends for GTG‑enabled tags because, unlike Basic Consent Mode (which simply blocks the tag until a default is set), it is **compatible with manual GTG setups**: it lets the Google tag load and send privacy‑safe, cookieless pings even while consent is denied or not yet known, and switches to full measurement as soon as the visitor's choice is received — without depending on the exact order in which the GTG script and the consent banner load.

To enable it with Commanders Act:

* Enable **Advanced Consent Mode** in your Commanders Act Google Consent Mode configuration — see [Google Consent Mode in Commanders Act TMS](https://doc.commandersact.com/features/consent-management/setup-guides/tag-manager/google-consent-mode-in-commanders-act-tms) and [Google Tag Manager (GTM) – Consent Mode](https://doc.commandersact.com/features/consent-management/setup-guides/tag-manager/google-tag-manager-gtm-consent-mode).
* Enable **Data Transmission Controls** in your Google tag settings (Google Ads, GA4, or Campaign Manager 360) to independently restrict advertising, analytics, and diagnostics data while consent is denied — see [Data transmission controls](https://support.google.com/google-ads/answer/16054531).
* Set **Global Consent Defaults** for your Google tag so a baseline (denied, unless required otherwise) consent state always applies per region, even in the rare case where the CMP stub cannot be guaranteed to run first — see the [region-specific behavior section of Google's consent mode guide](https://developers.google.com/tag-platform/security/guides/consent#region-specific_behavior) and [GTM's Consent Overview settings](https://support.google.com/tagmanager/answer/10718549?hl=en).

{% hint style="success" %}
Choose the right template! In case you need to enable Google Consent Mode with IAB TCF, use our TCF IAB [banner templates](https://doc.commandersact.com/features/consent-management/user-guides/privacy-banners/banner-templates) (Footer or Popin) and follow the [setup specifications mentioned here](https://doc.commandersact.com/features/consent-management/setup-guides/tag-manager/google-consent-mode-in-commanders-act-tms#additional-settings)
{% endhint %}

***

## Architecture

With **Commanders Gateway**, you reserve a **single path** on your domain, for example:

```
https://example.com/mypath/
```

* **Google scripts** (gtag.js / gtm.js) are loaded directly from `/mypath/`.
* **Other vendor scripts** (Meta, Snapchat, Bing, Awin, etc.) are served from `/mypath/js/` with an **obfuscated filename** generated by Commanders Act.

Example:

```
https://example.com/mypath/js/f4558899203.js
```

The mapping between each vendor and its obfuscated script filename is provided in the **Commanders Act First-Party Hosting interface**.

**Diagram (conceptual):**

```
Website  →  example.com/mypath/ (Google tags)
         →  example.com/mypath/js/f4558899203.js (Meta, Snap, Bing…)
         →  Commanders Gateway  →  Vendor endpoint
```

***

## Cookie filtering and governance

Some organizations, especially those with strict privacy policies, may have concerns about sending **first-party cookies to external partners** such as Google. Commanders Gateway supports **data minimization** and provides mechanisms to control which cookies can transit through the gateway. Two complementary approaches can be used :

#### Cookie blacklisting at the edge

Customers can filter cookies **directly at the CDN or edge layer** (Cloudflare Worker, Fastly Compute, etc.). This can be done by **simply configuring the Worker code provided in this guide** (see CloudFlare free or Faslty tab below) to remove specific cookies before the request is forwarded to Commanders Gateway.

This allows specific cookies to be removed from the request **before it reaches Commanders Gateway**, ensuring that only the cookies approved by the organization leave its infrastructure.

#### Cookie whitelisting before forwarding to partners

Commanders Gateway can also enforce a **cookie whitelist when forwarding requests to partners**.

For example, when forwarding measurement requests to Google, the gateway can be configured to **only include Google-related cookies** (such as `_ga` or `_gcl_*`).\
All other cookies are automatically excluded from the request sent to Google.

## Before you begin

This guide assumes your website is already configured with:

* A tag management system (Commanders Act, Google Tag Manager, or equivalent).
* A CDN or load balancer (Cloudflare, Akamai, Fastly, Nginx, etc.) that can forward requests to external endpoints.

***

## Step 1: Choose the tag serving path

You must reserve **one path** on your website domain.

Example:

```
/mypath
```

Caution: This setup reroutes all traffic with the chosen path. To avoid affecting your website, choose a path that's not already in use.

***

## Step 2: Route traffic

{% tabs %}
{% tab title="Cloudflare Enterprise" %}
When using Cloudflare Enterprise, we recommend using a **Cloudflare Worker** to proxy all traffic from your chosen path, for example `/mypath`, to Commanders Gateway infrastructure.

This approach is the same as the Cloudflare Free setup. It is more reliable than trying to route the path with Cloudflare Origin Rules, because the Worker gives full control over the request URL, headers, cookie filtering, and geolocation forwarding.

**Step 1: Create the Worker**

1. In the Cloudflare dashboard, go to **Workers & Pages** → **Create application** → **Worker**.
2. Copy/paste the following code:

```javascript
const prefix = "/mypath"; // Example path, replace with the path you choose in the previous step
const sid = "12345"; // Example workspace ID (aka site ID), replace with your own ID

// List of cookie names that must NOT be forwarded to Commanders Gateway. You can add your technical cookies if needed
const blacklistedCookies = [
  "PHPSESSID",
  "JSESSIONID"
];

addEventListener("fetch", event => {
  event.respondWith(handleRequest(event.request));
});

function filterCookieHeader(cookieHeader, blacklist) {
  if (!cookieHeader) return "";

  const blacklistSet = new Set(blacklist);

  const filteredCookies = cookieHeader
    .split(";")
    .map(cookie => cookie.trim())
    .filter(cookie => {
      const cookieName = cookie.split("=")[0];
      return !blacklistSet.has(cookieName);
    });

  return filteredCookies.join("; ");
}

async function handleRequest(request) {
  const url = new URL(request.url);

  if (url.pathname.startsWith(prefix)) {
    // Construct target URL. It replaces ${sid} with your workspace/site ID above.
    const targetUrl = `https://s${sid}.commander4.com${url.pathname}${url.search}`;

    // Clone request headers
    const newHeaders = new Headers(request.headers);
    newHeaders.set("X-Forwarded-Host", url.host);

    const country = request.cf?.country || "";
    const region = request.cf?.region || "";

    if (country) newHeaders.set("X-Forwarded-Country", country);
    if (region) newHeaders.set("X-Forwarded-Region", region);
    if (country && region) {
      newHeaders.set("X-Forwarded-CountryRegion", `${country}-${region}`);
    }

    // Filter the Cookie header before proxying the request.
    const cookieHeader = newHeaders.get("Cookie");
    const filteredCookies = filterCookieHeader(cookieHeader, blacklistedCookies);

    if (filteredCookies) {
      newHeaders.set("Cookie", filteredCookies);
    } else {
      newHeaders.delete("Cookie");
    }

    // Remove Host header to avoid conflicts
    newHeaders.delete("host");

    // Proxy request to Commanders Gateway infra
    const proxyRequest = new Request(targetUrl, {
      method: request.method,
      headers: newHeaders,
      body: request.body,
      redirect: "follow"
    });

    return fetch(proxyRequest);
  }

  return new Response("Not Found", { status: 404 });
}
```

This Worker proxies requests while adding extra headers:

* `X-Forwarded-Host`
* `X-Forwarded-Country`
* `X-Forwarded-Region`
* `X-Forwarded-CountryRegion`

It can also filter sensitive or technical cookies before forwarding the request to Commanders Gateway.

**Step 2: Bind the Worker to the path**

1. In Cloudflare, open your domain settings.
2. Navigate to **Workers Routes**.
3. Add a new route with:
   * **URL pattern**: `www.example.com/mypath*`
   * **Worker**: select the Worker created in step 1.

Once saved, all requests to `/mypath` will be proxied to Commanders Gateway.

**Step 3: Verify the setup**

You can verify the setup by navigating to:

```
https://example.com/mypath/g/healthy
```

Note : the default google subpath is /g/ but it could be customized. This google subpath is located immediately after /mypath/ .

It should return:

```
ok
```

To verify geolocation forwarding, you can also test:

```
https://example.com/mypath/g/?validate_geo=healthy
```

It should also return:

```
ok
```
{% endtab %}

{% tab title="Cloudflare Snippet" %}
Cloudflare Snippets provide a lighter alternative to a full Worker for proxying the Commanders Gateway path. A Snippet runs JavaScript at the edge and is associated with a **Snippet rule** that determines which requests execute it.

{% hint style="info" %}
Cloudflare Snippets are available on **Pro, Business, and Enterprise** plans. The hostname used for the gateway must be proxied through Cloudflare.
{% endhint %}

**Step 1: Create the Snippet**

1. In the Cloudflare dashboard, open your domain.
2. Go to **Rules** → **Snippets**.
3. Create a new Snippet and give it a descriptive name, for example `Commanders Gateway`.
4. Paste the following code:

```javascript
const CONFIG = {
  prefix: "/mypath", // Replace with the gateway path chosen for your website
  targetBase: "https://s1234.commander4.com", // Replace 1234 with your workspace/site ID
  blacklistedCookies: [
    "PHPSESSID",
    "JSESSIONID"
  ]
};

function filterCookieHeader(cookieHeader, blacklist) {
  if (!cookieHeader) return "";
  const blacklistSet = new Set(blacklist);
  return cookieHeader
    .split(";")
    .map(c => c.trim())
    .filter(c => {
      const name = c.split("=")[0].trim();
      return !blacklistSet.has(name);
    })
    .join("; ");
}

export default {
  async fetch(request) {
    const url = new URL(request.url);

    if (!url.pathname.startsWith(CONFIG.prefix)) {
      return new Response("Not Found", { status: 404 });
    }

    const remainingPath = url.pathname.slice(CONFIG.prefix.length) || "/";
    const targetUrl = `${CONFIG.targetBase}${CONFIG.prefix}${remainingPath}${url.search}`;

    const newHeaders = new Headers(request.headers);

    newHeaders.set("X-Forwarded-Host", url.host);
    newHeaders.set("X-Forwarded-Proto", "https");

    const country = request.cf?.country || "";
    const region = request.cf?.region || "";
    if (country) newHeaders.set("X-Forwarded-Country", country);
    if (region) newHeaders.set("X-Forwarded-Region", region);
    if (country && region) {
      newHeaders.set("X-Forwarded-CountryRegion", `${country}-${region}`);
    }

    const cookieHeader = newHeaders.get("Cookie");
    const filteredCookies = filterCookieHeader(cookieHeader, CONFIG.blacklistedCookies);
    if (filteredCookies) {
      newHeaders.set("Cookie", filteredCookies);
    } else {
      newHeaders.delete("Cookie");
    }

    newHeaders.delete("host");

    const proxyRequest = new Request(targetUrl, {
      method: request.method,
      headers: newHeaders,
      body: request.body,
      redirect: "manual"
    });

    const response = await fetch(proxyRequest);

    if (response.status >= 300 && response.status < 400) {
      return new Response(response.body, {
        status: response.status,
        headers: response.headers
      });
    }

    return response;
  }
};
```

**Step 2: Customize the configuration**

Update the values at the top of the Snippet:

* `prefix`: replace `/mypath` with the path reserved for Commanders Gateway on your domain.
* `targetBase`: replace `s1234.commander4.com` with the Commanders Gateway endpoint associated with your workspace/site ID.
* `blacklistedCookies`: add any session, sensitive, or internal cookies that must not be forwarded to Commanders Gateway.

The Snippet also forwards the visitor's country and region through `X-Forwarded-Country`, `X-Forwarded-Region`, and `X-Forwarded-CountryRegion`.

Redirect responses from Commanders Gateway are intentionally returned to the browser instead of being automatically followed at the edge.

**Step 3: Configure the Snippet rule**

Associate the Snippet with a rule that only matches your Commanders Gateway path.

For example, in the Expression Editor:

```
starts_with(http.request.uri.path, "/mypath")
```

Replace `/mypath` with the same path configured in `CONFIG.prefix`.

{% hint style="warning" %}
Keep the Snippet rule and `CONFIG.prefix` synchronized. If they use different paths, requests may not be proxied as expected.
{% endhint %}

Deploy the Snippet after testing it with Cloudflare's preview tools.

**Step 4: Verify the setup**

After deployment, verify:

* `https://example.com/mypath/healthy` → should return `ok`.
* `https://example.com/mypath/?validate_geo=healthy` → should return `ok` when geolocation forwarding is correctly configured.
* Cookies listed in `blacklistedCookies` are no longer present in requests received by Commanders Gateway, while other cookies are preserved.
{% endtab %}

{% tab title="Cloudflare Free" %}
When using Cloudflare Free, the setup relies on a **simple Worker** that proxies all traffic from your chosen path (e.g. `/mypath`) to Commanders Gateway infrastructure.

**Step 1: Create the Worker**

1. In the Cloudflare dashboard, go to **Workers & Pages** → **Create application** → **Worker**.
2. Copy/paste the following code:

```javascript
const prefix = "/mypath"; // Example path, replace with the path you choose in the previous step
const sid = "12345"; // Example workspace ID (aka site ID), replace with your own ID

// List of cookie names that must NOT be forwarded to Commanders Gateway. You can add your technical cookies if needed
const blacklistedCookies = [
  "PHPSESSID",
  "JSESSIONID"
];

addEventListener("fetch", event => {
  event.respondWith(handleRequest(event.request));
});

function filterCookieHeader(cookieHeader, blacklist) {
  if (!cookieHeader) return "";

  const blacklistSet = new Set(blacklist);

  const filteredCookies = cookieHeader
    .split(";")
    .map(cookie => cookie.trim())
    .filter(cookie => {
      const cookieName = cookie.split("=")[0];
      return !blacklistSet.has(cookieName);
    });

  return filteredCookies.join("; ");
}

async function handleRequest(request) {
  const url = new URL(request.url);
  if (url.pathname.startsWith(prefix)) {
    // Construct target URL (it replaces ${sid} with your workspace/site ID above)
    const targetUrl = `https://s${sid}.commander4.com${url.pathname}${url.search}`;

    // Clone request headers
    const newHeaders = new Headers(request.headers);
    newHeaders.set("X-Forwarded-Host", url.host);

    const country = request.cf?.country || "";
    const region = request.cf?.region || "";
    if (country) newHeaders.set("X-Forwarded-Country", country);
    if (region) newHeaders.set("X-Forwarded-Region", region);
    if (country && region) {
      newHeaders.set("X-Forwarded-CountryRegion", `${country}-${region}`);
    }

    // Filter the Cookie header before proxying the request.
    const cookieHeader = newHeaders.get("Cookie");
    const filteredCookies = filterCookieHeader(cookieHeader, blacklistedCookies);

    if (filteredCookies) {
      newHeaders.set("Cookie", filteredCookies);
    } else {
      newHeaders.delete("Cookie");
    }

    // Remove Host header to avoid conflicts
    newHeaders.delete("host");

    // Proxy request to Commanders Gateway infra
    const proxyRequest = new Request(targetUrl, {
      method: request.method,
      headers: newHeaders,
      body: request.body,
      redirect: "follow"
    });
    return fetch(proxyRequest);
  }
  return new Response("Not Found", { status: 404 }); // Return 404 if request path does not match prefix
}
```

This Worker proxies requests while adding extra headers (`X-Forwarded-Host`, `X-Forwarded-Country`, `X-Forwarded-Region`).

**Step 2: Bind the Worker to the path**

1. In the Cloudflare, open your domain settings.
2. Navigate to **Workers Routes**.
3. Add a new route with:
   * **URL pattern**: `www.example.com/mypath*`
   * **Worker**: select the Worker created in step 1.

Once saved, all requests to `/mypath` will be proxied to Commanders Gateway.
{% endtab %}

{% tab title="Akamai" %}
{% hint style="warning" %}
Commanders Gateway with Akamai is in **beta**. If you have a question or issue with your setup, reach out the support
{% endhint %}

**Create the redirect rule**

1. Create a new version of your delivery configuration in **Property Manager**.
2. Under the **Property Configuration Settings** section, add a new Rule:
   * Name it: _Route measurement_
3. Add a new **Match**:
   * Match type: `Path`
   * Condition: _is one of_
   * Value: `/mypath/*`
4. Add a new **Behavior**:
   * Select _Standard Property Behavior_ and choose **Origin Server** behavior.
   * Set **Origin Server Hostname** to `s1234.commander4.com.`
   * Set **Forward Host Header** to _Origin Hostname_.
5. Save the new rule and deploy your changes.
   * ⚠️ Test the redirect rule in your **staging environment** before rolling out to production.
   * Ensure no other rules modify/remove outgoing response headers (e.g., _Content-Type_) as this may break scripts.

***

**Include geolocation information**

1. Navigate to the **Property Variables** section and add the following variables:

| Variable name | Security settings |
| ------------- | ----------------- |
| USER\_REGION  | Hidden            |
| USER\_COUNTRY | Hidden            |

2. Choose your **Redirect rule** (created above) under Property Configuration Settings.
3. Add two new **Set Variable** behaviors (one per variable):

| Variable              | Create Value From | Get Data From  | Edgescape Field | Operation |
| --------------------- | ----------------- | -------------- | --------------- | --------- |
| PMUSER\_USER\_REGION  | Extract           | Edgescape Data | Region Code     | None      |
| PMUSER\_USER\_COUNTRY | Extract           | Edgescape Data | Country Code    | None      |

4. Add two new **Modify Outgoing Request Header** behaviors:

| Action | Select Header Name | Custom Header Name  | Header Value                     |
| ------ | ------------------ | ------------------- | -------------------------------- |
| Add    | Other...           | X-Forwarded-Region  | \{{user.PMUSER\_USER\_REGION\}}  |
| Add    | Other...           | X-Forwarded-Country | \{{user.PMUSER\_USER\_COUNTRY\}} |

5. Save the new rule and deploy your changes.

***

**Filter cookies before forwarding to Commanders Gateway**

You can prevent specific cookies from being forwarded to Commanders Gateway. This can be useful for session cookies, cookies containing sensitive information, or internal technical cookies that should not leave your infrastructure.

The list of cookies to exclude depends on your organization's requirements.

**Option 1: Use Akamai cookie management capabilities**

If cookie management behaviors are available with your Akamai configuration, configure Akamai to remove the relevant cookies from the request before it is forwarded to Commanders Gateway.

For example, you may want to exclude cookies such as:

```
PHPSESSID
JSESSIONID
```

Configure the behavior so that these cookies are removed from the **client request sent to the origin**, where the origin is your Commanders Gateway endpoint.

{% hint style="info" %}
The exact name and availability of Akamai cookie management behaviors can vary depending on the Akamai products enabled on your account.
{% endhint %}

**Option 2: Modify the outgoing Cookie header**

If cookie management capabilities are not available, you can use a **Modify Outgoing Request Header** behavior on the `Cookie` header and remove selected cookies using a regular expression.

Example for `PHPSESSID` and `JSESSIONID`:

```regex
(?:^|;\s*)(PHPSESSID|JSESSIONID)=[^;]*
```

Configure:

* **Header:** `Cookie`
* **Action:** Regex Replace
* **Regular expression:** the expression above, adapted to your cookie list
* **Replacement:** empty

{% hint style="warning" %}
Test this configuration carefully before deploying it to production. An incorrect regular expression may result in a malformed `Cookie` header or unintentionally remove cookies that should be forwarded.
{% endhint %}

If you use several CDN or edge configurations for the same implementation, keep the cookie exclusion list consistent across them.

***

**Verify the setup**

After deploying the Akamai configuration:

* Navigate to `https://example.com/mypath/healthy` → should display `ok`.
* Test geolocation headers: `https://example.com/mypath/?validate_geo=healthy` → should also display `ok`.
* Verify that requests forwarded to Commanders Gateway no longer contain the excluded cookie names, while other cookies are still forwarded normally.
{% endtab %}

{% tab title="Fastly" %}
{% hint style="warning" %}
Fastly support for Commanders Gateway is currently in **beta**. The steps below are intended for technical users familiar with Fastly Compute (Compute Services). Depending on your Fastly account setup (domains, TLS, products enabled), some production binding steps can vary.
{% endhint %}

When using Fastly, the setup is different from Cloudflare. You deploy a **Compute service** (Wasm) and configure it mainly via the **Fastly API and CLI** from a terminal.

**Prerequisites**

1. Create an API token in the Fastly interface (scopes must allow Compute, services, backends, and deployments).
2. Export the token in your terminal environment:

```
export FASTLY_API_TOKEN=XXXXXXXXXXXX
```

3. Install prerequisites:

* Node.js
* Fastly CLI

**Step 1: Create the Compute service**

Create a new Compute service:

```
fastly service create --name "CA Gateway" --type wasm
```

Fastly returns a **service ID**, for example:

```
dyBxiT8wpc2c8ZQg2KRrMN
```

Save it, you will need it for backend creation and deployments.

**Step 2: Create a local Compute project (starter kit)**

Generate a local project from the default JavaScript starter kit:

```
npm create @fastly/compute@latest -- --language=javascript --default-starter-kit
```

This creates a project structure similar to:

```
.
├── README.md
├── fastly.toml
├── package.json
└── src
    ├── index.js
    └── welcome-to-compute.html
```

**Step 3: Configure the service ID in fastly.toml**

Edit `fastly.toml` and set the service ID:

```
# fastly.toml
service_id = "YOUR_SERVICE_ID"
```

**Step 4: Create the backend (Commanders Gateway origin)**

Create a backend that points to the Commanders Gateway infrastructure (replace `1234` with your workspace/site ID):

```
fastly backend create \
  --service-id YOUR_SERVICE_ID \
  --version 1 \
  --name commander_gateway \
  --address s1234.commander4.com \
  --use-ssl \
  --port 443 \
  --ssl-sni-hostname s1234.commander4.com
```

Notes:

* `--version 1` is a typical starting point. If your service already has versions, use the version you intend to deploy.
* The backend address must be `s1234.commander4.com` (your own workspace/site ID).

**Step 5: Implement the routing logic in src/index.js**

Replace the content of `src/index.js` with the following worker code.

You must update:

* `prefix` (your customer path, example: `/mypath`)
* `sid` (your Commanders workspace/site ID, example: `s1234`)

```javascript
/// <reference types="@fastly/js-compute" />

import { env } from "fastly:env";
import { includeBytes } from "fastly:experimental";

const prefix = "/PATHACHANGER";              // TODO: replace with your chosen gateway path (e.g. "/mypath")
const sid = "s123456";                       // TODO: replace with your workspace/site ID (e.g. "s1234")
const BACKEND = "commander_gateway";         // Fastly backend name pointing to sid.commander4.com

const STRIP_PREFIX = true;                   // If true, removes the prefix from the forwarded path
const PREPEND_PATH = "/gateway";             // Internal gateway entrypoint on Commanders side (do not change)

// List of cookie names that must NOT be forwarded to Commanders Gateway. Add your technical cookies if needed
const blacklistedCookies = [
  "PHPSESSID",
  "JSESSIONID"
];

addEventListener("fetch", (event) => event.respondWith(handleRequest(event.request)));

function filterCookieHeader(cookieHeader, blacklist) {
  if (!cookieHeader) return "";

  const blacklistSet = new Set(blacklist);

  const filteredCookies = cookieHeader
    .split(";")
    .map(cookie => cookie.trim())
    .filter(cookie => {
      const cookieName = cookie.split("=")[0];
      return !blacklistSet.has(cookieName);
    });

  return filteredCookies.join("; ");
}

async function handleRequest(request) {

  const url = new URL(request.url);

  // Only proxy requests that match the configured prefix
  if (!url.pathname.startsWith(prefix)) {
    return new Response("Not Found", { status: 404 });
  }

  // Build the path that will be forwarded to Commanders Gateway
  let fwdPath = url.pathname;

  // Optionally strip the customer prefix (e.g. "/mypath") so the origin receives "/"
  if (STRIP_PREFIX) {
    fwdPath = fwdPath.slice(prefix.length) || "/";
  }

  // Prepend Commanders internal entrypoint (required)
  if (PREPEND_PATH) {
    fwdPath = PREPEND_PATH + fwdPath;
  }

  // Final origin URL on Commanders infrastructure
  const target = `https://${sid}.commander4.com${fwdPath}${url.search}`;

  // Clone headers and add forwarding info
  const headers = new Headers(request.headers);
  headers.set("X-Forwarded-Host", url.host);

  // Forward geo information when available (optional but recommended)
  const country = (request.geo && request.geo.country_code) ? request.geo.country_code.toUpperCase() : "";
  const region  = (request.geo && request.geo.region) ? request.geo.region : "";
  if (country) headers.set("X-Forwarded-Country", country);
  if (region)  headers.set("X-Forwarded-Region", region);
  if (country && region) headers.set("X-Forwarded-CountryRegion", `${country}-${region}`);

  // Filter the Cookie header before proxying the request.
  const cookieHeader = headers.get("Cookie");
  const filteredCookies = filterCookieHeader(cookieHeader, blacklistedCookies);

  if (filteredCookies) {
    headers.set("Cookie", filteredCookies);
  } else {
    headers.delete("Cookie"); // Remove the Cookie header entirely if all cookies were filtered out
  }

  // Avoid Host header conflicts at origin
  headers.delete("host");

  // Rebuild the request for the origin
  const originReq = new Request(target, {
    method: request.method,
    headers,
    body: request.body
  });

  // Bypass cache to ensure measurement hits are never cached
  const co = new CacheOverride("pass");

  // Send request to the configured Fastly backend
  return fetch(originReq, { backend: BACKEND, cacheOverride: co });

}
```

Important:

* Replace `s1234.commander4.com` with your real workspace/site ID endpoint.
* Keep the same `prefix` as the path you reserve on the customer domain (example: `/mypath`).
* Do NOT add a trailing slash at the end of the path in customer-side URLs.

**Step 6: Deploy**

Deploy the Compute service:

```
npm run deploy
```

**Step 7: Test**

After deployment, Fastly provides a temporary domain for testing, for example:

```
https://plainly-rested-bison.edgecompute.app/mypath/healthy
```

It should return:

```
ok
```

**Production binding (customer domain)**

At this stage, the Compute service runs on a Fastly-provided test domain. To go live on the customer domain (example: `https://example.com/mypath/`), you still need to bind the service to the production domain and ensure TLS is in place.

This typically involves, depending on the customer setup:

* Adding the customer domain to the Fastly service, and configuring TLS for it (managed TLS or customer certificate).
* Creating the required DNS record (often a CNAME) so `example.com` points to Fastly.
* Ensuring the Compute service is the one receiving requests for the chosen path (example: `/mypath*`) on that domain.

Because the exact steps depend on the Fastly products enabled on the account and how the customer manages TLS and DNS, treat this as a beta step and reach out to support if you need the exact commands for your specific setup.
{% endtab %}
{% endtabs %}

***

## Step 3: Update the scripts in your tag management system or your website

Replace vendor script URLs with the new **first-party paths**.

Examples:

### Google

```html
<!-- Instead of -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-12345"></script>

<!-- Use -->
<script async src="/mypath/"></script>
```

### Meta (Facebook Pixel)

```html
<!-- Instead of -->
<script src="https://connect.facebook.net/en_US/fbevents.js"></script>

<!-- Use (obfuscated path provided in the Commanders Act interface) -->
<script src="/mypath/js/f4558899203.js"></script>
```

### Snapchat

```html
<script src="/mypath/js/a82b99df732.js"></script>
```

### Bing (UET)

```html
<script src="/mypath/js/c77ac91be11.js"></script>
```

Each obfuscated filename is automatically generated and available in the **Commanders Act First-Party Hosting interface**.

### OneTag

You can manually change the domain of your cact() setup with the `collectionDomain` propery Exemple :

```javascript
cact(..., {collectionDomain: "www.youdomain.com/mypath"});
```

Warning : do NOT add a `/` at the end of the path

***

## Step 4: Verify setup

* For the global path, check the health endpoint:
  * `https://example.com/mypath/healthy` → should return `ok`
* Use browser DevTools to verify that:
  * Google scripts are loaded from `/mypath/`
  * Other vendor scripts are loaded from `/mypath/js/{obfuscated}.js`
  * Requests are made to your **first-party domain**.
* Ensure events appear in the respective partner dashboards (Google Analytics, Facebook Events Manager, etc.).

***

## Benefits

* **Durability**: Tracking continues to work even with Safari ITP and third-party cookie restrictions.
* **Resilience**: Serving scripts from your domain with obfuscated filenames makes it more difficult for blocking rules to interfere.
* **Centralized setup**: A single path (`/mypath`) manages all vendors.
* **Future-proof**: Adapts to privacy sandbox and upcoming browser restrictions.
*

## Configure first party data collection for Commanders Act features (via Gateway)

This chapter explains how to route Commanders Act data collection through your **first party gateway path** (for example `/mypath`) for the main Commanders Act features.

Important notes:

* The gateway path shown in examples (`/mypath`) is only an example. Customers choose their own path when setting up the gateway in their CDN or edge tool (Cloudflare, Akamai, etc.).
* All examples below assume your gateway is healthy: `https://example.com/mypath/healthy` returns `ok`.

***

### 1. Server-side destinations via the gateway (example: Meta Facebook CAPI)

Commanders Act server-side tracking relies on **oneTag** tags. Typically, you will have one oneTag per event you want to collect, for example:

* `page_view`
* `add_to_cart`
* `purchase`

To route these oneTag events through the gateway, you must update the **oneTag tag configuration** so that the `cact()` setup uses your first party collection domain and path.

In your oneTag tag (or in the shared snippet used by your oneTag tags), set `collectionDomain`:

```javascript
cact(..., { collectionDomain: "www.yourdomain.com/mypath" });
```

Notes:

* Replace `www.yourdomain.com/mypath` with your own domain and the path you configured in your gateway.
* Do NOT add a trailing `/` at the end of the path.
* Once this is set, all oneTag events (page\_view, add\_to\_cart, purchase, etc.) will be collected via your first party gateway path.

***

### 2. CDP, Campaign Analytics and CMP collection via the gateway

_(Data Activation, Campaign Analytics, CMP statistics and proof of consent)_

These three features rely on the same routing mechanism. To send their data through the gateway, you must define the variable **`tC.clientCollectDns`** either:

* directly inside each relevant tag, **or**
* in a **global configuration tag** that runs before all Commanders Act tags (recommended).

Example:

```javascript
tC.clientCollectDns = "www.yourdomain.com/mypath";
```

Behavior:

* As soon as `tC.clientCollectDns` is defined, collection for **Data Activation, Campaign Analytics, and CMP-related tracking** will be made via the gateway.
* `mypath` is only an example. Customers can use any path they configured in their gateway setup.

Implementation options:

* **Option A (simple):** add the line directly inside the Data Activation / Campaign Analytics / CMP tag.
* **Option B (recommended):** add it in a global configuration tag that runs before all Commanders Act tags.

***

### Verification checklist

After applying the changes above, verify:

* The gateway health endpoint: `https://example.com/mypath/healthy` returns `ok`.
* In browser DevTools (Network tab), Commanders Act collection requests go to your first party domain and path (for example `https://example.com/mypath/...`).
* Events and data appear as expected in:
  * Server-side destination dashboards (example: Meta Events Manager for CAPI)
  * Data Activation flows
  * CMP statistics and proof of consent reporting (when applicable)
  * Campaign Analytics reporting
