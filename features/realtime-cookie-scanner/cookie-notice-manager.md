# Cookie Notice Manager

### Introduction

The **Cookie Notice Manager** lets you review, edit, and publish your cookies list on your website.

### Manage Cookie Information

Cookies are organized into three lists :

1. **New** – recently detected, **unreviewed**.
2. **Active** – validated by you, ready to be shown on the notice.
3. **Ignored** – (optional) You can place cookies here that you do not want to see listed in your cookie notice.

{% hint style="success" %}
The cookie manager interface reflects the current status of your site in real time. When you refresh the page, the “New” section may contain cookies that have just been detected a few seconds ago.
{% endhint %}

Each entry can be edited (✎) to adjust vendor, category, storage type, domain, duration, and description.\
You can also add custom cookies or activate/deactivate existing ones.

<figure><img src="../../.gitbook/assets/image (84).png" alt="" width="329"><figcaption></figcaption></figure>

> Keep internal cookies in _Ignored_ to prevent reappearance after future scans.

| **Name**             | <p>Name of cookie e.g. _ga<br>*In case of multiple (more than 3) cookies with common pattern, they re grouped by patterns</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | <ul><li>Tag client-side</li><li>Chrome Extension</li></ul>                         |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Vendor**           | Name of the vendor that uses the cookie e.g. Google                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | <ul><li>Cookie Database</li></ul>                                                  |
| **Category**         | Category of the cookie that give a high level information on the purpose of the cookie e.g. Technical Cookie                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | <ul><li>Cookie Database</li></ul>                                                  |
| **Storage Location** | <p>Storage location of the cookie (combination of cookie type and storage domain). It has one of the following values:</p><ul><li>1st Party Cookie (<a href="http://www.example.de/">www.example.de</a>)</li><li>3rd Party Cookie (www.example.de)</li><li>HttpOnly 1st Party Cookie (<a href="http://www.example.de/">www.example.de</a>)</li><li>HttpOnly 3rd Party Cookie (<a href="http://www.example.de/">www.example.de</a>)</li><li>localStorage (<a href="http://www.example.de/">www.example.de</a>)</li><li>sessionStorage (<a href="http://www.example.de/">www.example.de</a>)</li></ul><p>The domain in brackets is the domain where the cookie is stored. For 1st party cookies it is the domain or subdomain of the website. For 3rd party cookies it is a 3rd party domain or subdomain that is different from the website.</p> | <ul><li>Tag client-side</li><li>Chrome Extension</li></ul>                         |
| **Storage Duration** | <p>Storage duration of the cookie. An algorithm is used to smoothen technical inaccuracies and to optimise readability for users:</p><ul><li>For Session Cookies it displays "Session"</li><li>Under 1 month it displays in days, e.g. "7 days"</li><li>Above 1 month it displays in month, e.g. "13 months"</li><li>Above 36 month it displays in years, e.g. "5 years".</li><li>Above 100 years it displays “Unlimited”</li></ul><p>Local storage always has duration "Unlimited" and session storage always has duration "Session".</p>                                                                                                                                                                                                                                                                                                      | <ul><li>Tag client-side</li><li>Chrome Extension</li><li>Cookie Database</li></ul> |
| **Description**      | Description for what the cookie is used, e.g. “Base64 UUID used to identify users on this website to optimise usage across sessions. Used on all pages.”                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | <ul><li>Cookie Database</li></ul>                                                  |
| **Website**          | <p>Domain(s) of the website(s) the cookie is scanned.<br>For 1st party cookies, the full URL of the latest scan is also displayed</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | <ul><li>Tag client-side</li><li>Chrome Extension</li></ul>                         |

#### Custom Fields & Filters

* Add custom fields via Settings (⚙️) to store extra info.
* Filter by host, language, storage type, or 3rd-party domain.
* A frequency slider hides rare cookies (< 5 % by default).

{% hint style="info" %}
Cookie scanner doesn't store cookie's values
{% endhint %}

<figure><img src="../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

#### Occurrence frequency

For all types of cookies & storage you can visualize the percentage of detection frequency

<figure><img src="../../.gitbook/assets/image (534).png" alt=""><figcaption></figcaption></figure>

#### Settings

Need to declare a new domain, or add a new language?

You can do it directly in the side panel "settings"

<figure><img src="../../.gitbook/assets/image (123).png" alt="" width="407"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (121).png" alt="" width="347"><figcaption></figcaption></figure>

#### Exempted Flag

To help you to see the exempted cookies set before consent, you can add an "exempted" flag. Simply activate the dedicated switch in "Cookie Edition"

This will helps you to identify quickly the cookies that are allowed to be set without consent user

<figure><img src="../../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (127).png" alt="" width="318"><figcaption></figcaption></figure>

#### Translations by IA

Our IA feature can translate cookie descriptions in any language.\
Translate all your cookie descriptions in one click.\
\
You get up to 200 free translations per day.\
Need more? Come back tomorrow and you'll receive another 200 free credits!\
\
To translate all your cookies, use the 'Settings' option (one target language allowed at a time).

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Do you need to translate just one cookie into many languages?\
Then use the 'Edit Cookie' function:

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Our tool will translate your cookies for all languages that have an "empty" description.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

***

### Manage Cookie Notice

`Health > Realtime Cookie Scanner > Cookie Notice Manager > DEPLOY (Tab)`

The **DEPLOY** tab is used to install, create, and publish the cookie notice on your website.\
It shows all existing notice versions and their status.

#### Install Cookie Notice

Once the cookie information is set up in the **EDIT** tab, you can install the cookie notice in three formats :

**1. JavaScript Snippet**

Paste the JavaScript snippet on your legal page to automatically generate and display the cookie list table.

<figure><img src="../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

**2. HTML Table (recommended)**

The HTML table is the recommended installation method for a dynamic cookie notice.\
Create a placeholder `<div>` in your CMS and use the tag template “TRUST | Install Cookie Notice” in your Web Container.\
Both must share the same ID (e.g. `ca-slot--cookie-notice`).

**Endpoint of the HTML file :**

```
https://cdn.tagcommander.com/cookie-scanner/<site_id>/v1/cookies-<language_code>.html
```

* **site\_id** = your Commanders Act site ID (e.g. 1234)
* **language\_code** = language of the cookie notice (default = `en`)

> ℹ️ The HTML table uses accessible semantic markup and inherits your site’s CSS.\
> You can fully customize its style with your own stylesheet.

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

**3. JSON API**

For advanced or custom use cases, the JSON API returns the cookie information in a structured format that can be used in web apps or native apps.

**Endpoint of the JSON file :**

```
https://cdn.tagcommander.com/cookie-scanner/<site_id>/v1/cookies-<language_code>.json
```

* **site\_id** = your Commanders Act site ID
* **language\_code** = language code (e.g. `fr`, `en`)

{% hint style="info" %}
By default all cookies are listed but it is also possible to manage one cookie notice per website
{% endhint %}

***

#### Create a New Version

Click **NEW VERSION** to generate a new cookie notice based on the current Active cookies.\
You can add an internal comment to describe the changes.

#### Preview a Version

Use the **Play button (▶️)** to preview any version.\
Preview does not apply your site styling.

#### Export a Version

Click the **Download icon (⬇️)** to export all localizations in `HTML`, `JSON`, `CSV`, or `XLSX`.\
Each language is included as a separate file (or tab in XLSX).

#### Deploy a Version

Press **DEPLOY** to publish a cookie notice version on your site.\
You can also roll back to a previous version if needed.

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

***

### Labels and Meanings

| Label              | Meaning                                                                                         |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| **scanned**        | Detected on live user sessions.                                                                 |
| **new**            | Newly found cookie pending review.                                                              |
| **missing**        | Previously seen cookie not been scanned for over one month                                      |
| **before-consent** | Cookie set before user consent.                                                                 |
| **inferred**       | The 3rd-party cookie was inferred via the cookie database from a known 3rd-party domain request |
| **custom**         | Manually created cookie record.                                                                 |

***

### Alerts and Integrations

* Instant alerts (< 60 s) on new or non-compliant cookies.
* Configurable by language, and severity.
* Integrations : Email, Webhook, Slack, Microsoft Teams.

<figure><img src="../../.gitbook/assets/image (60).png" alt="" width="375"><figcaption></figcaption></figure>
