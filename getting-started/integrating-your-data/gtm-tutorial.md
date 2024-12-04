---
description: 'Quick Setup: From GTM Client-Side to Commanders Act Server-Side'
---

# GTM Tutorial

This guide shows you how to quickly set up server-side event forwarding for GA4 in Google Tag Manager (GTM) using Commanders Act. With this setup, your GA4 events can be routed to multiple destinations like Facebook CAPI, Google Enhanced Conversions, and others.

1. **Create a GTM Source** in Commanders Act.
2. **Update the GA4 URL** in GTM.
3. **Set Up Domain Delegation** for first-party data collection (strongly recommended).

{% hint style="info" %}
#### Alternative Approach for Event Tracking

Instead of using GA4 to transfer events, you can add **Commanders Act tags** directly in GTM for each event you want to track. While this method takes more time to set up, it gives you full control over which events are sent, independent of GA4, and works even if GA4 is not used.

For more details, check the [Commanders Act GTM template documentation](https://doc.commandersact.com/features/sources/sources-catalog/web/gtm).
{% endhint %}

## Step 1: Create a GTM Source in Commanders Act

1. Log in to **Commanders Act**.
2. Go to the **Sources** section and create a new **Google Tag Manager** source.\
   ![](<../../.gitbook/assets/image (2) (1).png>)
3. **Copy the Source Token** displayed.

<figure><img src="../../.gitbook/assets/image (1) (1) (3).png" alt=""><figcaption></figcaption></figure>

## Step 2: Update GA4 in Google Tag Manager

1. Open your **GTM** workspace.
2. Find your **GA4 Configuration Tag**.
3.  In the **Tag Configuration** window, under **Fields to Set**, add a new field with the following values:

    * Field Name: `server_container_url`
    *   Value:

        ```bash
        https://collect.commander1.com/events?tc_s={siteId}&token={sourceKey}&&ga_url_param=
        ```

    Replace:

    * **{siteId}**: Your Commanders Act site ID.
    * **{sourceKey}**: The Source Token from Commanders Act.

**Note:** This URL uses Commanders Act’s default domain (`commander1.com`) to get you up and running quickly. For better data quality, it’s strongly recommended to use your own custom domain (see Step 3).

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

4. **Save** and **Publish** your changes in GTM.

## Step 3: Set Up Domain Delegation for First-Party Data Collection

For enhanced data accuracy and first-party tracking, we recommend setting up a custom domain through **domain delegation**. This ensures the data is collected and processed as first-party, improving tracking reliability and compliance with privacy regulations.

#### How to Set Up Domain Delegation:

1. Go to the **Domain Management** section of Commanders Act (find detailed instructions [here](../../configure/administration/domain-management/)) and follow the steps to configure a custom subdomain such as https://collect.yourdomain.com
2.  In GTM, update `server_container_url`with your subdomain url such as:&#x20;

    ```bash
    https://collect.yourdomain.com/events?tc_s={siteId}&token={sourceKey}&&ga_url_param=
    ```

    Replace `collect.yourdomain.com` with your own subdomain.

Using a custom domain not only improves tracking precision but also helps ensure better compliance with browser and privacy policies.

### Step 4: Event Forwarding to Multiple Destinations

Once GA4 events are sent to Commanders Act, they can be forwarded to various destinations, such as: Facebook CAPI, Google Enhanced Conversion, Bing Ads, TikTok, Awin, ... And many more through the Commanders Act plug\&play destinations catalog.

## Going Further: Bypassing Ad-Blockers with GTM Script Proxification

For users looking to optimize server-side tracking, Commanders Act provides also an option to **proxify the GTM JavaScript file** to bypass ad-blockers. This solution ensures that consented data can still flow to your analytics tools or partners without being unfairly blocked by ad-blockers that might indiscriminately block GTM scripts, even when used responsibly.

#### How It Works:

* Instead of using the default GTM URL (e.g., `https://www.googletagmanager.com/gtm.js?id=XXX`), the script is served from your own domain (e.g., `https://track.yourdomain.com/custompath.js`) with a unique path modifier to avoid detection by ad-blockers.
* This process helps ensure that **only user-consented data** is collected and forwarded, in strict compliance with privacy regulations such as GDPR.

#### A Privacy-Respectful Approach:

Our server-side infrastructure is designed with **privacy, consent, and user control** at its core. By proxifying the GTM script, you're simply ensuring that **consented data** can be processed and sent to trusted tools and partners, in line with the user’s preferences. This aligns with best practices in privacy and GDPR compliance, ensuring that ad-blockers do not unfairly interrupt responsible data flows.

If you're interested in setting this up, please **contact your account manager** for more information.
