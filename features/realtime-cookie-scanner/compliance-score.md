# Compliance Score

### Overview

The **Compliance Summary** provides a clear and actionable view of your website’s cookie compliance based on data collected by the Cookie Scanner.

It enables you to:

* Evaluate your overall compliance level
* Identify the most critical issues
* Prioritize actions to improve your setup

***

### Filters

Use the filters at the top of the page to refine the analysis:

* **Rare Cookies**: Include or exclude low-frequency cookies (Off by default)
* **Website**: Select the domain(s) configured in your Cookie Notice settings

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

***

### Cookie Compliance Score

The **Cookie Compliance Score** (out of 100) reflects your website’s compliance level.

The score is calculated based on:

* Cookies set before user consent
* Cookies set after user refusal
* Cookie purpose (marketing cookies have a higher impact)

A low score indicates significant GDPR compliance risks, while a higher score reflects better alignment with regulatory requirements.

Example:

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

***

### Executive Narrative

The **Executive Narrative** provides an automated summary of your compliance status.

It highlights:

* The main issues affecting your score
* Key risk areas
* High-level recommendations to improve compliance

Example:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

***

### Next Best Actions

The **Next Best Actions** section displays the top 3 actions with the highest impact on your compliance score.

Each recommendation includes:

* Cookie name & Category
* Detection frequency
* Issue type (e.g. before consent, after refusal)
* Severity & estimated impact on the score

#### Priority indicators

* **High impact**: Major issues with strong impact on the score (10 points or more)
* **Medium impact**: Important issues (between 5 and 9 points)
* **Low impact**: Minor issues or easy fixes (less than 5 points)

Example:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

***

### Key Metrics

The following indicators provide a quick overview of your situation:

* **Cookies before consent**: Number of cookies set before user approval
* **Cookies after refusal**: Cookies set after a user has refused consent
* **High frequency issues**: Number of recurring issues identified
* **Total cookies scanned**: Total number of cookies detected in the last 30 days

Example:

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

***

### Cookies by Consent Status and Category

This chart shows the distribution of cookies by:

* Consent status: before consent, after consent, after refusal
* Category: essential, analytics, marketing, uncategorized

This helps identify which types of cookies are not compliant and when they are triggered.

Example:

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

***

### Top Violations

The **Top Violations** section lists the cookies with the highest negative impact on your compliance score.

* Up to 5 cookies are displayed
* If fewer cookies significantly impact the score, only relevant ones are shown

Focus on these cookies first to achieve the fastest improvements.

Example:

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

***

### Best Practices

To improve your compliance score:

* Do not set non-essential cookies before consent
* Ensure user refusal is fully respected
* Use the [flag "exempted"](https://doc.commandersact.com/features/realtime-cookie-scanner/cookie-notice-manager#exempted-flag) for cookies allowed to be set before consent, or after refuse all
* Properly categorize all cookies
* Regularly review high-impact issues identified in the interface

{% hint style="info" %}
Have you changed your settings to improve your score? \
You’ll need to wait 5 minutes for the changes to take effect on this page, whilst your score is being recalculated
{% endhint %}
