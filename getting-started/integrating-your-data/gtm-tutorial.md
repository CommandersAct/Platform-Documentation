---
description: 'Quick Setup: From GTM Client-Side to Commanders Act Server-Side'
---

# GTM Tutorial

This guide shows you how to quickly set up server-side event forwarding for GA4 in Google Tag Manager (GTM) using Commanders Act. With this setup, your GA4 data can be routed to multiple destinations like Facebook CAPI, Google Enhanced Conversions, and others. For optimal performance, it is strongly recommended to implement **first-party domain delegation**.

### Step 1: Create a GTM Source in Commanders Act

1. Log in to **Commanders Act**.
2. Go to the **Sources** section and create a new **Google Tag Manager** source.
3. **Copy the Source Token** displayed.

### Step 2: Update GA4 in Google Tag Manager

1. Open your **GTM** workspace.
2. Find your **GA4 Configuration Tag**.
3.  In the **Tag Configuration** window, under **Fields to Set**, add a new field with the following values:

    * Field Name: `server_container_url`
    *   Value:

        ```bash
        https://collect.commander1.com/events?tc_s={siteId}&token={sourceKey}&ga4_param=
        ```

    Replace:

    * **{siteId}**: Your Commanders Act site ID.
    * **{sourceKey}**: The Source Token from Commanders Act.

**Note:** This URL uses Commanders Act’s default domain (`commander1.com`) to get you up and running quickly. For better data quality, it’s strongly recommended to use your own custom domain (see Step 3).

4. **Save** and **Publish** your changes in GTM.

### Step 3: Set Up Domain Delegation for First-Party Data Collection

For enhanced data accuracy and first-party tracking, we recommend setting up a custom domain through **domain delegation**. This ensures the data is collected and processed as first-party, improving tracking reliability and compliance with privacy regulations.

#### How to Set Up Domain Delegation:

1. Go to the **Domain Management** section of Commanders Act (find detailed instructions [here](../../configure/cookies/first-domain-tracking-phoenix.md)).
2.  Follow the steps to configure a custom subdomain such as:

    ```arduino
    https://track.yourdomain.com/events?tc_s={siteId}&token={sourceKey}&ga4_param=
    ```

    Replace `yourdomain.com` with your own domain.

Using a custom domain not only improves tracking precision but also helps ensure better compliance with browser and privacy policies.

### Step 4: Event Forwarding to Multiple Destinations

Once GA4 events are sent to Commanders Act, they can be forwarded to various destinations, such as: Facebook CAPI, Google Enhanced Conversion, Bing Ads, TikTok, Awin, ... And many more through the Commanders Act plug\&play destinations catalog.
