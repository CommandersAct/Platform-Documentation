# Consent Analysis

The Commanders Act **Consent Analysis Dashboard** provides a centralized view of your compliance health and user engagement. It combines high-level visual modules with deep analytical metrics to help you optimize your consent rates and tracking quality.

## Visual Analysis Modules

The dashboard is organized into specialized widgets to provide immediate insights without digging into raw tables.

### 1. Executive KPI Cards

These cards provide a weighted average of your selected banners and include **Period-over-Period (PoP)** comparisons.

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

* **Global Consent Rate:** Total percentage of visitors who accepted at least one category.
* **Interaction Rate:** Percentage of visitors who actively engaged with the banner (Accept, Refuse, or Configure).
* **Explicit Consent (Trust Metric):** Measures the choice of visitors who actually interacted with the UI, excluding "ghost traffic" or bounces. This is your most accurate indicator of brand trust.
* **Estimated Tracking Loss:** Quantifies data loss by distinguishing between **Explicit Refusals** (active choice) and **No Choice** (visitors who left without interacting).

### 2. Decision Journey (Funnel)

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

The Funnel widget visualizes the conversion path to identify where drop-offs occur:

1. **Exposure:** Total visitors who saw the CMP banner.
2. **Interaction:** Visitors who engaged with a button or link on the first layer.
3. **Opt-ins:** Final volume of visitors who provided a positive consent.

### 3. Strategic Insights

The dashboard automatically interprets data to highlight growth levers.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### 4. Segmentation & Compliance

* **Geographic Impact:** Segments performance between **Europe (GDPR)** and the **Rest of the World**.
* **Consent by Device:** Compares Desktop, Mobile, and Tablet performance.
* **Real-time Cookie Scanner:** A live audit of your compliance health. It displays your **Compliance Score**, detected **Violations** (e.g., cookies dropped before consent), and **New Cookies** discovered.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

***

## Interface & Controls

### Filter Options

You can customize the dashboard by adjusting filter settings at the top left. By default, the top 10 banners that have at least 1,000 views are displayed.

{% tabs %}
{% tab title="PRIVACY" %}
Configures which privacy banners are displayed in the dashboard modules and table.
{% endtab %}

{% tab title="DEVICE" %}
Allows to filter dashboard metrics for typical device types. Depending on the browser settings of your website visitors, device recognition might not be 100% accurate.
{% endtab %}

{% tab title="USER LOCATION" %}
Allows to filter dashboard metrics for data inside and outside the EU.
{% endtab %}
{% endtabs %}

<figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-feaa0f05a6bee3e45aab0d473801440195944e6a%2Fimage.png?alt=media" alt=""><figcaption><p>Filter interface</p></figcaption></figure>

### Time Selection & Trends

On the top right, specify a date range. The dashboard displays **Trends** (green/red percentages) comparing the selected period to the previous one of equal length.

{% hint style="info" %}
To select only one day, click the same day twice in the date picker so that both the start and end date are identical.
{% endhint %}

### Export Options

Export CSV reports via the **EXPORT** button.

{% hint style="warning" %}
Data collection is real-time, but advanced metrics calculation (deduplication, bot filtering) is updated **overnight**. For immediate raw data, use the export option in "Data Governance > Consent Management > Settings".
{% endhint %}

***

## Measurement Approach & Logic

Commanders Act Consent Analysis measures privacy banner interactions based on **visitors/traffic**, not unique users.

### Deduplication (TCPID Cookie)

A 1st party cookie `TCPID` is set to deduplicate actions.

* Commanders Act identifies visitors as new if they delete this cookie.
* The dashboard uses a **last-action-of-the-day** logic: only the final interaction recorded during a 24-hour period is kept for calculations.

### Defining Actions

{% tabs %}
{% tab title="Optin actions" %}
An optin action occurs when a visitor:

* Clicks the **Accept** button.
* Saves the Privacy Center with at least one category set to "on".
* Navigates to a second page, clicks an element, or scrolls (only if **Implicit Consent** is enabled in your settings).
{% endtab %}

{% tab title="Optout actions" %}
An optout action occurs when a visitor:

* Clicks the **Reject** button.
* Saves the Privacy Center with all categories set to "off".
{% endtab %}
{% endtabs %}

***

## Scenarios & Detailed Examples

The following scenarios explain how deduplication affects your KPIs:

#### **Example 1: Same-day change**

1. A new visitor accepts the privacy banner.
2. Later that same day, they open the Privacy Center and **revoke** their consent.

* **Result:** The dashboard records **1 Opt-out** action (the last action) and **1 deduplicated banner view**.
* **Final Metrics:** Opt-in rate: 0%, No choice rate: 0%, Opt-out rate: 100%.

#### **Example 2: Multi-day journey**

1. **Day 1:** A visitor arrives, does not interact with the banner, and leaves.
2. **Day 2:** The visitor returns, accepts the banner, then later revokes it via the Privacy Center.

* **Day 1 Data:** 1 banner view, 100% No Choice.
* **Day 2 Data:** 1 banner view, 100% Opt-out (based on the last action).
* **Full Period View:** If you select both days, the metrics will show an **Opt-in rate of 0%**, a **No choice rate of 50%**, and an **Opt-out rate of 50%**.

***

## Detailed Metric Reference

### Global Metrics

{% hint style="warning" %}
On **23/09/2021** the calculation method was updated to include both banner displays and Privacy Center displays.
{% endhint %}

| Metric                      | Description                                                                                   |
| --------------------------- | --------------------------------------------------------------------------------------------- |
| **Visitors exposed to CMP** | Number of visitors viewing a CMP screen (Banner or Privacy Center).                           |
| **Give consent**            | Visitors who consent to at least one category. Only the last action of the day is kept.       |
| **Do not give consent**     | Visitors who consent to no category. Includes both explicit rejects and "no choice" visitors. |

### Consent & Interaction Methods

| Metric                             | Description                                                                   |
| ---------------------------------- | ----------------------------------------------------------------------------- |
| **Banner button**                  | Explicit consent via the "Accept" button on the first layer.                  |
| **Privacy center**                 | Explicit consent by saving settings within the Privacy Center.                |
| **Implicit (Browse/Click/Scroll)** | Consent triggered by user behavior (if configured).                           |
| **Interaction rate**               | Percentage of visitors who clicked _any_ button, link, or the Privacy Center. |

### Engaged Visitors (Explicit Choice)

| Metric                                 | Description                                                                        |
| -------------------------------------- | ---------------------------------------------------------------------------------- |
| **Visitors making an explicit choice** | Number of visitors who clicked either Accept, Reject, or saved the Privacy Center. |
| **Explicitly consent**                 | Visitors who made a choice and chose to consent.                                   |
| **Explicitly reject**                  | Visitors who made a choice and chose to reject. Excludes "No Choice" bouncers.     |

### Privacy Center Usage

| Metric                              | Description                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| **Exposed to Categories/Vendors**   | Number of visitors viewing the category or vendor lists.     |
| **Visitors saving a configuration** | Number of visitors clicking the "Save" button in the PC.     |
| **Visitors not saving**             | Visitors who opened the PC but left the site without saving. |

***

## Advanced Understanding

### No Choice vs. Bounce Rate

In an opt-in configuration, bounce rate tracking is often impossible as bouncers leave before consenting to analytics. The **No Choice** metric is a valuable proxy for bounce rate.

* **Normal cases:** Visitors leaving immediately, or browsing without closing a non-blocking banner.
* **Special cases:** Internal redirects (e.g., language redirects), mobile app redirects, or bot/crawler traffic.

### A/B Testing

Privacy banner performance is critical for data-driven marketing. We recommend performing **A/B tests** to minimize "No Choice" and "Opt-out" rates. Use the **PRIVACY** filter to compare two banner versions side-by-side.

<figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-d13dc65265e88a7a5fdcf3022079fa637375cabf%2Fimage.png?alt=media" alt=""><figcaption><p>A/B testing comparison</p></figcaption></figure>
