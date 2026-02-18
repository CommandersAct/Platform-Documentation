---
cover: ../../.gitbook/assets/Gemini_Generated_Image_qik7qqik7qqik7qq.png
coverY: 0
---

# Cookies by Category

### Introduction

With the **Cookies by Category** interface, you get a clear view of all cookies detected on your site — by category and by consent status. It helps you quickly know:

* how many cookies you have in each category,
* how cookies are distributed across categories,
* when cookies fire (before consent, after consent),
* and detailed info for each cookie (name, vendor, domain, frequency, etc.).

Think of it as your cookie-audit dashboard: fast overview, detailed breakdown.

***

### Components

#### Category Summary Cards

At the top, there are four cards — **Essential**, **Analytics**, **Marketing**, and **Others**.\
Each card displays:

* the category name
* the total number of cookies detected in that category

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

**What you can do**\
Click any card to focus on one category — the rest of the dashboard updates automatically to show only cookies from that category. The selected card gets a visual highlight.

***

#### Rare Cookies filter

The rare cookies filter is OFF by default. It means that rare cookies are NOT displayed (all cookies with an occurence rate lower than 5%)\
If you need to see the rares cookies on this UI, simply turn ON the switch button

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

#### Category Share Donut Chart

Just below the cards, a donut chart shows how cookies are split across categories (Essential / Analytics / Marketing / Others).

**What you can do**\
Click a segment to filter the entire dashboard on that category — same effect as clicking the card. The clicked segment and corresponding card get highlighted.

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

#### Consent-Status & Category Bar Chart

This chart shows the number of cookies per category depending on the consent status:

* **Before consent**
* **After consent**

It helps you spot if any cookies are firing too early (before consent) or after “Refuse all” (a possible compliance issue).

{% hint style="info" %}
Our dev team is currently working to detect the status "After refuse all" (optout consent), to detect cookies created when the visitor consent is "Optout"\
This new information will be available soon!
{% endhint %}

***

#### 🔍 Detailed Cookie Table

Below, a table lists every detected cookie with the following columns:

| Column           | Detail                                                                                                            |
| ---------------- | ----------------------------------------------------------------------------------------------------------------- |
| Cookie name      | Name/key of the cookie                                                                                            |
| Vendor           | The vendor or script source                                                                                       |
| Domain           | Domain tied to the cookie                                                                                         |
| Duration         | Cookie lifetime or expiration info                                                                                |
| % Occur.         | Percentage of pageviews (or visits) where the cookie appears                                                      |
| Detection status | The state when the cookie was detected: Before consent / After consent (compliant) / After Refuse all (violation) |

Above the table you’ll find a **Detection Status** dropdown filter with options:

* All
* Before consent
* After consent



**Filtering logic**

* Combine category + status filters: you can filter by category **and** detection status at the same time.
* If you change only the detection status (and no category), the donut chart and the cards stay neutral — they don’t highlight anything.
* If you have a category selected and then select a status, the table shows only cookies matching both.

***

### Resetting & Filter Controls

* You can reset the category filter (to show “All categories”) using the **All** button — but any detection-status filter stays applied.
* The date-range selector (as shown in the mockup) is currently disabled. The default value is “Last 30 days.” No “vs previous period” comparison for now.

***

### How to use — Suggested Workflow

1. Open the page — you’ll see all cookies by default.
2. Use the cards or donut chart if you want to focus on a category (e.g. only Marketing cookies).
3. Use the detection-status dropdown if you want to check cookies fired before consent, after consent, or after “Refuse all.”
4. Combine both filters to zoom in on exactly what you want (e.g. Marketing cookies that fired after user refused all).
5. Reset category filters while keeping status filter if needed (via “All” button).

***

### Why this matters

This screen helps you:

* understand how many cookies you have per category,
* check whether non-essential cookies respect user consent settings,
* locate potential compliance issues (cookies firing before consent or after refusal),
* and inspect each cookie in detail.

It’s a powerful tool to support privacy compliance and give you clear visibility on cookies behavior.
