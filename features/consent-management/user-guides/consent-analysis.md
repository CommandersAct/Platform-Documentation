# Consent Analysis

The Commanders Act Consent Analysis dashboard provides insights into critical KPIs of your consent management setup.

## Interface

### Filter options

The dashboard provides KPIs for each individual Commanders Act Consent banner. You can customize the dashboard by adjusting filter settings at the top left of the interface. Commanders Act Consent Analysis provides the following filters:

{% tabs %}
{% tab title="PRIVACY" %}
Configures which privacy banners are displayed in the dashboard table.
{% endtab %}

{% tab title="DEVICE" %}
Allows to filter dashboard metrics for typical device types. Depending on the browser settings of your website visitors, device recognition might not be 100% accurate.
{% endtab %}

{% tab title="USER LOCATION" %}
Allows to filter dashboard metrics for data inside and outside the EU.
{% endtab %}
{% endtabs %}



{% hint style="info" %}
Now the top 10 banners that have at least 1,000 views are displayed. To view other banners, use the PRIVACY selection menu
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

### Time selection

On the top right you will find options to filter data for a specific time range by specifying a start and end date. The dashboard will show metrics including the selected start and end date.

{% hint style="info" %}
To select only one day, the day has to be clicked twice in the date picker so that both the start and end date are set to the needed day.
{% endhint %}

### Export options

It is possible to export CSV reports via the EXPORT option on the top right in the interface. Reports will only include data for the selected timeframe.

{% hint style="warning" %}
Data collection is done in real-time, but metrics calculation is updated overnight, therefore no data is available in the dashboard for the current day (if you need immediate data, you can export the raw consent data via the "Data Governance > Consent Management > Settings" page).
{% endhint %}

## Measurement approach

Commanders Act Consent Analysis measures privacy banner interactions to calculate consent KPIs.

All metrics are visitor/ traffic based and not user based. Commanders Act Consent Banner therefore sets a 1st party cookie TCPID on website visitors. It deduplicates certain metrics (e.g. opt-in actions) of a visitor based on this cookie. Commanders Act identifies visitors as new visitors in case they delete this cookie.

### Optin vs. optout action

To understand dashboard metrics it is important to understand how Commanders Act Consent Analysis measures optin and optout actions.&#x20;

{% tabs %}
{% tab title="Optin actions" %}
An optin action occurs when a visitor...

* clicks the accept button of the privacy banner**.**
* saves the privacy center with at least one category set to "on".
* navigates to a second page (only in case implicit "on navigation" consent was installed).
* scrolls on the landing page (only in case implicit "on scroll" consent was installed).
* clicks any element on the website (only in case implicit "on click" consent was installed).
{% endtab %}

{% tab title="Optout actions" %}
An optout action occurs when a visitor...

* clicks the reject button of the privacy banner.
* saves the privacy center with all categories off.
{% endtab %}
{% endtabs %}

### Examples

Following examples outline a hypothetical scenario with only one website visitor to explain the measurement approach:

#### **Example 1**

1. A new visitor arrives at a website with a Commanders Act Consent banner.
2. He accepts the privacy banner and immediately navigates to the privacy policy page.
3. There he re-opens the privacy center and revokes his prior consent.

This would lead to one optin action and one optout action and two banner views. Commanders Act Consent Analysis deduplicates action and therefore only uses the last action of a visitor to calculate the consent KPIs per day. Additionally it deduplicates the banner views per visitor per day therefore only counts one banner view in this scenario. This user journey leads to an optin rate of 0%, a no choice rate of 0%, and optout rate of 100%.

#### **Example 2**

1. A new visitor arrives at a website with a Commanders Act Consent banner.
2. He does not interact with the banner and leaves the site immediately.
3. On the next day he returns to the website.
4. He accepts the privacy banner and immediately navigates to the privacy policy page.
5. There he re-opens the privacy center and revokes his prior consent.

On the first day this would lead to no action and one deduplicated banner view. On the second day this leads to one deduplicated optout action (see Example 1) and one deduplicated banner view.

For a selected timeframe that only includes the first day this would result in a no choice rate of 100%. For a selected timeframe that only includes the second day this would result in a optout rate of 100%. For a selected timeframe that includes both days this would result in an optin rate of 0%, a no choice rate of 50%, and an optout rate of 50%.

{% hint style="warning" %}
This measurement approach and the following metrics are based on the standard usage of Commanders Act Consent banners templates. In case of a banner customization or custom workflow, part of the metrics might have a different meaning.
{% endhint %}

## Dashboard metrics

Following you will find detailed descriptions of each metric in the dashboard.\
When available you can expand the line to get the break down by categories.

### Global

{% hint style="warning" %}
Metrics are deduplicated each day.\
On **23/09/2021** the calculation method has changed to take into account both banner displays and Privacy Center displays (previously, only banner displays were taken into account). When displaying the dashboard after this date, **every date range** will take into account Privacy Center display.
{% endhint %}

| Metric                      | Description                                                                                                                                                                                                                                                                                                                                                |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Visitors exposed to CMP** | <p></p><p>The number of visitors viewing a screen of the CMP for the requested time period.<br>It includes visitors viewing the first layer as well as visitors opening the privacy center.</p>                                                                                                                                                            |
| **Give consent**            | <p></p><p>The number of visitors who at least consent to one category.<br>It includes consent collected via the first layer (accept all, reject all buttons) as well as consent collected via the privacy center.<br>In case several consent actions are collected during the same day (consent, no consent), only the last one is taken into account.</p> |
| **Do not give consent**     | <p></p><p>The number of visitors who consent to no category.<br>It includes visitors who explicitly don’t give consent (e.g. click reject all button) and “no choice visitors” with no action recorded.<br>In case several consent actions are collected during the same day (consent, no consent), only the last one is taken into account.</p>           |

### Consent methods

| Metric                               | Description                                                                                                               |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| **Banner button**                    | The number of visitors who explicitly consent to all categories by clicking the accept button on the first layer.         |
| **Privacy center**                   | The number of visitors who explicitly consent to at least one category by clicking the save button on the privacy center. |
| **Implicit** > **Continue browsing** | The number of visitors who implicitly consent to all categories by navigating to a second page on the website.            |
| **Implicit** > **Page click**        | The number of visitors who implicitly consent to all categories by clicking any element on the page.                      |
| **Implicit** > **Page scroll**       | The number of visitors who implicitly consent to all categories by scrolling down on the page.                            |

### How engaged visitors react to CMP?

| Metric                                       | Description                                                                                                                                                                                                                                                                                                                                |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Visitors making an explicit choice**       | <p>The number of visitors saving a consent choice.<br>It includes choices made by clicking consent or refuse buttons on the first layer as well as choices saved via the privacy center.</p>                                                                                                                                               |
| **Explicitly consent (at least 1 category)** | <p>The number of visitors who at least consent to one category.<br>It includes consent collected via the global layer (accept all, reject all buttons) as well as consent collected via the privacy center.</p>                                                                                                                            |
| **Explicitly reject**                        | The number of visitors who consent to no category. It only includes visitors who explicitly don’t give consent (e.g. click reject all button). It excludes “no choice visitors” with no action recorded. In case several consent actions are collected during the same day (consent, no consent), only the last one is taken into account. |

### How visitors interact with the CMP banner?

| Metric               | Description                                                                                                                                                                                                       |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Interaction rate** | <p>The number of visitors who at least interact with one element of the CMP first layer.<br>It includes clicks on accept button, reject button, configure button (opening the privacy center) and text links.</p> |

### How visitors use the privacy center?

| Metric                                            | Description                                                                                                                                                                                                                     |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Visitors exposed to privacy center categories** | The number of visitors viewing the category section of the privacy center for the requested time period.                                                                                                                        |
| **Visitors exposed to privacy center vendors**    | The number of visitors viewing the vendor section of the privacy center for the requested time period.                                                                                                                          |
| **Visitors saving a configuration**               | <p>The number of visitors clicking the privacy center save button.<br>It includes visitors using the save button as well as the accept all or reject all buttons.</p>                                                           |
| **Visitors not saving a configuration**           | <p>The number of visitors viewing the privacy center and not saving a configuration.<br>It includes visitors using the closing cross to go back to the first layer and visitor leaving the website from the privacy center.</p> |

## Understanding metrics

### No choice vs. Bounce rate

In an optin configuration (no tracking before a user provides consent), bounce rate tracking is not possible anymore as bouncers usually won't interact with the website and therefore won't provide consent for analytic services. The no choice metric of Commanders Act Consent Analysis can help to get an idea on your bounce rate, but it is not the same metric!

In a default optin configuration, the "no choice" is expected to include:&#x20;

**Normal cases:**

* Visitors who do not provide an optin and leave the website (bounce)
* Visitors who do not provide an optin and continue to browse the website without closing the privacy consent message (possible with header/ footer banner templates, less likely with a popin template that blocks website navigation)
* Visitors who do not provide an optin who continue browsing the website after closing the privacy consent message with the closing cross

**Special cases:**

* Visitors that are redirected by an internal redirect of the website (for example due to a language redirect on the landing page)
* Mobile visitors who are redirected to the mobile app when arriving on the landing page in a mobile browser
* Visits of bots like web crawlers. Common bot traffic is excluded but industry specific crawlers might increase "no choice" percentage

{% hint style="info" %}
At the time of the first release of Commanders Act Consent Analysis the no choice rate is expected to be close to your bounce rate. The metrics will then start to differ over the following time.
{% endhint %}

## AB testing

The performance of privacy banner is crucial for the success of any data driven marketing activity. Therefore it is especially important to perform AB tests of your privacy banner to improve the user experience of your website visitors and to improve your consent KPIs. For AB tests it is common to set a goal to minimise the no choice and optout KPIs.

Commanders Act Consent Analysis dashboard makes it very easy to compare metrics of two banners set up for AB test side by side by adding the AB test banners via the PRIVACY filter option.

<figure><img src="../../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Please contact your Commanders Act consultant in case you need support in setting up AB tests for your Commanders Act Consent setup.
{% endhint %}
