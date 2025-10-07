# Realtime Cookie Scanner

### 1. Introduction

The **Realtime Cookie Scanner (RCS)** is Commanders Act’s next-generation module for **continuous, intelligent, and real-world monitoring** of cookies and client-side storage (cookies, localStorage, sessionStorage, etc.).

Unlike crawler-based scanners that simulate visits with bots, the RCS observes **you real user sessions** — across all countries, devices, browsers, and contexts — providing a **complete, live picture** of what actually happens in your users’ browsers.

Whether a cookie appears only for **specific users, browsers, countries, forgotten landing pages, or A/B test variants**, RCS detects it.\
No missed edge cases, no blind spots, no delayed snapshots.

***

### 2. Typical Use Cases

RCS provides Privacy, Marketing, and Technical teams with **instant, exhaustive, and actionable visibility** over every cookie and storage item.

**Common use cases include:**

* **Continuous CNIL / GDPR compliance monitoring**\
  Detect any cookie deposited before consent and stay compliant in real time.
* **Instant audit after container or tag deployment**\
  Ensure new releases haven’t introduced unauthorized cookies.
* **Proactive detection of new or undeclared partners**\
  Identify scripts depositing unexpected cookies.
* **Automatic multilingual cookie policy publication**\
  Generate and publish an auto-translated cookie table that stays up to date.
* **Post-release monitoring during redesigns or migrations**\
  Detect regressions or compliance issues immediately.

***

### 3. Key Features

#### 🔍 100 % Real-World Detection

* Observes every real user session — no crawlers, no simulations.
* Detects cookies triggered by clicks, scrolls, mobile interactions, or dynamic tags.
* Lists **all URLs** where each cookie was found.
* Groups **variants of the same cookie** (dynamic names or hashed suffixes).
* Displays **detection frequency** (e.g. 0.2 % rare / 32 % common).
* Frequency filter lets you show or hide rare cookies.
* Covers **all countries and devices** at no extra cost.

#### 🧠 Knowledge Base & AI Classification

* Powered by a **large cookie database** enriched through Commanders Act’s browser extensions (Chrome & Edge), leveraging anonymized data from thousands of users.
* Auto-detects vendor, purpose, and category.
* Uses AI to find rare cookies description/category, with human validation.
* Automatically ranks cookies by risk and frequency.

#### ⚙️ Supported Storage Types

1st Party Cookies, 3rd Party Cookies, HttpOnly 1st Party Cookies, HttpOnly 3rd Party Cookies, localStorage, sessionStorage

#### 🔔 Realtime Alerts (< 60 s)

* Instant notifications for new, removed, or non-compliant cookies.
* Configurable by domain, language, and severity.
* Integrations : Email, Webhook, Slack, Teams.

#### 🌍 Multilingual Dynamic Cookie Table

* AI-translated, continuously updated table.
* Export in HTML, JSON, CSV, XLSX.
* Integrates with any website or CMP / TMS.

#### 📊 Live Dashboards

* Always up-to-date (real & realtime data, not batches).
* Breakdowns by vendor, category, domain, frequency, or status.
* Filters by domain, consent state, frequency, etc.

***

### 4. Setup and Configuration

Implementation is instant.

Your Commanders Act consultant or support simply activates RCS in the Backoffice.\
Once enabled, your Web Container injects the JS scanner and starts data collection.

> No scenarios to script, no login management, no maintenance.

RCS works immediately on real traffic — including logged-in or restricted pages.

> 💡 **Compatibility** : RCS is independent of the Commanders Act CMP or TMS and can be used with any CMP vendors or TMS vendors (GTM, etc.)

***

### 5. Interfaces & Roadmap

| Interface                 | Description                                                              | Status              |
| ------------------------- | ------------------------------------------------------------------------ | ------------------- |
| **Overview**              | Global summary of detected cookies and compliance status across domains. | 🧩 _In development_ |
| **New Cookies**           | Recently detected cookies with classification and alert options.         | 🧩 _In development_ |
| **Live Scan**             | Real-time feed of detections with domain and device filters.             | 🧩 _In development_ |
| **Cookie Origins**        | Trace pages, domains, and scripts that set each cookie.                  | 🧩 _In roadmap_     |
| **Cookies by Category**   | Breakdown by functional, analytics, ads, security.                       | 🧩 _In roadmap_     |
| **Compliance Summary**    | Overview of non-compliant cookies and risk levels.                       | 🧩 _In roadmap_     |
| **Cookie Notice Manager** | Manage, version, and publish the cookie table.                           | ✅ _Available_       |

***

### 6. Cookie Notice Manager

The **Cookie Notice Manager** is the evolution of the legacy Cookie Scanner interface, now part of RCS.\
It lets you review, edit, and publish your cookie information.

#### Manage Cookie Information

Cookies are organized into three lists :

1. **New** – recently detected, unreviewed.
2. **Active** – validated, shown on the notice.
3. **Ignored** – internal cookies, hidden from public view.

Each entry can be edited (✎) to adjust vendor, category, storage type, domain, duration, and description.\
You can also add custom cookies or activate/deactivate existing ones.

> Keep internal cookies in _Ignored_ to prevent reappearance after future scans.

#### Custom Fields & Filters

* Add custom fields via Settings (⚙️) to store extra info.
* Filter by host, language, storage type, or 3rd-party domain.
* A frequency slider hides rare cookies (< 5 % by default).

***

### 7. Manage Cookie Notice

`Health > Realtime Cookie Scanner > Cookie Notice Manager > DEPLOY (Tab)`

The **DEPLOY** tab is used to install, create, and publish the cookie notice on your website.\
It shows all existing notice versions and their status.

#### Install Cookie Notice

Once the cookie information is set up in the **EDIT** tab, you can install the cookie notice in three formats :

**1. JavaScript Snippet**

Paste the JavaScript snippet on your legal page to automatically generate and display the cookie list table.

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

***

### 8. Labels and Meanings

| Label              | Meaning                                                                                         |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| **scanned**        | Detected on live user sessions.                                                                 |
| **new**            | Newly found cookie pending review.                                                              |
| **missing**        | Previously seen cookie not been scanned for over one month                                      |
| **before-consent** | Cookie set before user consent.                                                                 |
| **inferred**       | The 3rd-party cookie was inferred via the cookie database from a known 3rd-party domain request |
| **custom**         | Manually created cookie record.                                                                 |

***

### 9. Alerts and Integrations

* Instant alerts (< 60 s) on new or non-compliant cookies.
* Configurable by domain, language, and severity.
* Integrations : Email, Webhook, Slack, Microsoft Teams.

***

### 10. Live Dashboards

RCS dashboards reflect the live state of your site in real time.\
They display active, new, and missing cookies and support filtering by partner, category, frequency, and compliance status.

***

### 11. User Rights

| User Right                 | Description                                                 |
| -------------------------- | ----------------------------------------------------------- |
| **View Cookie List**       | View the full list of detected cookies.                     |
| **Manage Cookie List**     | Edit cookies, add custom entries, and adjust fields.        |
| **Generate Cookie Notice** | Create a new cookie notice version.                         |
| **Deploy Cookie Notice**   | Publish or roll back notice versions.                       |
| **Manage Settings**        | Configure custom fields, filters, and frequency thresholds. |

***

### 12. AI Act compliancy

{% content-ref url="../getting-started/platform-interface/productivity-tools/commanders-ai.md" %}
[commanders-ai.md](../getting-started/platform-interface/productivity-tools/commanders-ai.md)
{% endcontent-ref %}
