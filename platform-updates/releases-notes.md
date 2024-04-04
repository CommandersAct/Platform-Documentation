---
description: >-
  All details about the updates or new features of each new release updated by
  our Product team!
---

# Release notes

## Release 10.0.22 - March 2024

**Mobile SDK Consent 5.2.1**\
🔧 Resolved a potential crash with Vendors details drop-down.\
➕ Added the Privacy Manifest file for enhanced security.\
🔨 Fixed Layout Constraints warnings on the purposes screen.\
🖼️ Ensured the Illustrations button always displays correctly.

_Benefits:_

* Smoother navigation without crashes.
* Enhanced privacy with manifest file integration.
* Improved layout stability for a seamless user experience.

***

**Mobile SDK Core 5.3.4, ServerSide 5.4.3, IAB 5.0.2**\
➕ All modules now feature the Privacy Manifest file.

_Benefits:_

* Heightened privacy measures across all platforms.

***

**New Destination: LinkedIn Conversions API**:link:\
🎉 Introducing the [LinkedIn CAPI](../features/destinations/destinations-catalog/linkedin\_capi.md) for direct marketing data connection.\
_Benefits:_

* Track campaign performance anywhere for optimized results.
* Better attribution and cost efficiency with complete data sets.

***

**New Destination: Firebase Analytics for Mobile Applications** :bulb:\
📱 Introducing a new informative configuration page for Firebase Analytics integration.\
_Benefits:_

* Seamless bridge between CMP & Firebase Analytics.
* Easy implementation of Google Consent Mode with Firebase Analytics (GA4).

<figure><img src="../.gitbook/assets/image (509).png" alt="" width="563"><figcaption></figcaption></figure>

***

**Security Enhancement!** :shield:\
🔒 Native platform login has been exclusively streamlined with SSO.

_Benefits:_

* Enhanced security with SSO-only access.
* Improved user experience without confusion.

***

**Speed Boost!** :fast\_forward:\
🚀 TMS client-side now limits displayed container versions at the generation step for efficiency.

_Benefits:_

* Eliminates timeouts and crashes during version generation.
* Clients can still access the latest 100 versions effortlessly.

***

**Real-time Destination's settings updates** :rocket:\
🚀 Modifications now propagate instantly across all servers for faster updates (settings, filters, activation, dry mode, etc.).

_Benefits:_

* No more waiting times, changes take effect instantly.
* Easy testing iterations for seamless destination adjustments.

***

**Introducing new "Reset Password" Page!** :key:\
🔑 Enjoy a user-friendly password reset experience.

_Benefits:_

* Simplicity: Visual widget for accurate input and ability to use passphrase
* Smartness: Progress bar for security evaluation.
* Solidity: Compliance with new standards for passphrase usage.

<figure><img src="../.gitbook/assets/image (510).png" alt="" width="375"><figcaption></figcaption></figure>

***

**New Destination: Taboola Events**\
🎉 New destination now available for server-side event tracking with [Taboola](../features/destinations/destinations-catalog/taboola/).

_Benefits:_

* Track conversions without client-side pixel installation.

***

Your feedback matters! Let us know how these updates enhance your Commanders Act experience. :smiley: [https://www.commandersact.com/en/contact/](https://www.commandersact.com/en/contact/)

## Release 10.0.21 - February 2024

🔧 **GA4 Source Update (Adloop)** 🔧&#x20;

* All GA4 conversion events now selectable as main conversions in Adloop&#x20;
* Events conditionable by custom variables (customEvent, customUser)

💡 **Benefits**:

* Comprehensive GA4 data-source connector
* Clients easily locate diverse GA4 conversions & events in Adloop
* Precise attribution calculation for better performance insights

***

🔍 **Dry mode enhancement** 🔍\
We had a smart credential cache management on our (closed beta) [dry mode](https://doc.commandersact.com/features/destinations/dry-mode-lab) feature on destinations.\
💡Benefits: Allow to not have Event Delivery polluted by false errors when you switch to OFF the dry mode

***

🚀 **Source Data Quality Boost** 🚀 \
🔍 Here's what's new:

🛠️ Faster interface loading for seamless user experience \
🛠️ Simplified menu for quicker access \
🛠️ Sneak peek into the Alerting system (closed beta) \
🛠️ Shortcut buttons for validation rules & Data Cleansing

✅ **Why it rocks**:

* Increased productivity with lightning-fast loading
* Simplified workflows for easier navigation
* Immediate issue detection for data quality perfection

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

***

🛡️ **New Privacy Template "popin accessibility"** 🛡️ \
🔒 New offerings for enhanced privacy & UX:

🔹 Ready-to-use privacy template for WCAG compliance \
🔹 Streamlined UX with improved information display

💡 **Why it's great**:

* WCAG compliance made simple
* Enhanced opt-in rates with new popin template
* Improved clarity for better user engagement

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

***

🚀 **Customer Spotlight: Amazon CAPI Integration** 🚀 \
🌟 Big shoutout to the team for wowing  users with our CAPI integration! 🌟

## Release 10.0.20 - January 2024

🌟 **Vue.js Wrapper Version Update** (TMS)🌟\
🔗 [Explore the Latest Release](https://github.com/CommandersAct/vue-tag-commander)

* **Compatibility Enhanced**: Now fully compatible with Vue3, ensuring a smoother integration for your web applications.
* **Why This Matters**: Seamless updates mean less downtime and more productivity for developers leveraging Vue.js in their projects.

***

🔍 **Live Event Inspector Enhancements** 🔍

* **Test Code Events Bypass**: Events with the `test_code` property can now bypass the standard sampling limit (2 millions stored logs max), guaranteeing visibility in high-traffic scenarios.
* **Increased Visibility for Test Code Events**: For events marked with `test_code`, there is now a generous sampling allowance of 100 events per minute per event type. This guarantees the visibility of these events for testing and validation purposes.
* **Filterable Test Codes**: The `test_code` property has been made searchable and filterable, simplifying the QA process.
* **Targeted Benefit**: Ideal for server-side feature users needing comprehensive event tracking, like mobile app production tests.

***

📦 **Amazon CAPI Destination Beta** 📦\
🔗 [Closed Beta Access](https://doc.commandersact.com/features/destinations/destinations-catalog/amazon/amazon-ads-conversions-api)

* **Exclusive Early Access**: Initially available to some customers, with potential openings for eager customers.
* **Why Join the Beta**: Influence the development of our Amazon CAPI destination and get a head start on leveraging this powerful integration.

***

🔧 **Smart Mapping for Google Enhanced Conversions** 🔧

* **Intuitive Automation**: Automatic mapping with the option for manual adjustments enhances data accuracy and utility.
* **Why It's Great**: Spend less time on setup and more on Data Governance with this smart, flexible feature.

<figure><img src="../.gitbook/assets/image (501).png" alt="" width="375"><figcaption></figcaption></figure>

***

🛠 **UX Enhancements Across Destinations** 🛠

* **Error Prevention**: Fields now have helpful prompts in red for incorrect inputs, reducing errors and improving data quality.
* **Why It Matters**: A more user-friendly interface leads to fewer mistakes and a smoother operation for our clients.

<figure><img src="../.gitbook/assets/image (500).png" alt="" width="274"><figcaption></figcaption></figure>

***

📈 **Significant User Enrichment Feature Upgrade** 📈

* **Advanced Data Enrichment**: Create complex formulas for dynamic [**user scoring**](../features/enrichments/augmented-user-attributes/) and attributes, all with a no-code approach.
* **Business Impact**: Drive targeted marketing actions and advanced customer segmentation, leading to improved ROI and analytics capabilities.

<figure><img src="../.gitbook/assets/image (496).png" alt="" width="331"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

***

📣 **CMP Feature Release: Google Consent Mode V2** 📣

* **Effortless Implementation**: Activate Google Consent Mode v2 easily, enhancing data collection quality while ensuring compliance.
* **Who Benefits**: Any client using Commanders Act Consent banners with Google tags, aiming for hassle-free RGPD compliance.

***

🌱 **Server-Side Architecture Eco-Efficiency** 🌱

* **Increased Efficiency**: We've optimized our architecture to process events more efficiently, significantly improving performance while minimizing our environmental footprint.

***

🔧 **Segmentation Engine v1 Update** 🔧

* **Refined Performance**: We've made incremental but meaningful updates to the Segmentation Engine v1, improving the efficiency of segment calculation times. This enhancement ensures smoother site personalization experiences.
* **Site Personalization Impact**: These improvements will subtly enhance the speed for websites to customize pages for each visitor, ensuring a more seamless user experience.
* **Looking Ahead**: Our development focus is on the Segmentation Engine v2 (currently in QA phase), which is set to bring groundbreaking performance and modernization that will take segmentation to the next level.

***

📲 **Facebook CAPI Now Supports Offline Conversions** 📲

* Send your offline conversion through your purchase event (type: offline)

***

📱 **Google Consent Mode Update for Android & iOS** 📱

* **Firebase Users**: Ensure seamless integration with the latest versions tailored for Android and iOS platforms.

***

🎹 **Piano Analytics Enrichment API Destination Released** 🎹

* **Data Enrichment Made Easy**: Seamlessly update transaction statuses or values, enriching your data landscape.

## Release 10.0.19 - December 2023

*   🔧 **Advanced Flexibility in Destination’s Consent Filters:** Get more flexibility for complex privacy setups \
    \
    You managing consent through our CMP while also utilizing a competitor's solution for different websites on the same account?\
    \
    You can now employ native privacy filters from either our CMP or an external solution within the same account !\


    <figure><img src="../.gitbook/assets/image (451).png" alt="" width="517"><figcaption></figcaption></figure>
*   📊 **Enhanced Event Collection Charts: Now More Insightful.** It's such easier to see the type of events collected! \


    <figure><img src="../.gitbook/assets/image (452).png" alt=""><figcaption><p><br></p></figcaption></figure>



*   🔒 **Data Governance: Introducing 'Tag & Data Sharing' Page.** In a quick view, control the shared Datas through the Client-Side TMS tags.\
    &#x20;_\*Please note: This is the preview v0 of this page. A nicer version is coming soon!_\


    <figure><img src="../.gitbook/assets/image (453).png" alt=""><figcaption></figcaption></figure>



*   🔑 **Streamlined Platform Administration Access**: Instant Workspace Access. No more need to log out and re login when you get access to a new site\
    \
    As an administrator, you granted access to a workspace to one of your colleague? He just need to refresh the page to see the site into the search bar's list. No need to log out and re-login anymore!\


    <figure><img src="../.gitbook/assets/image (449).png" alt="" width="329"><figcaption></figcaption></figure>



*   🌟 **Consistent and Upgraded Chart Styles Across the Platform** is now applied to all graphs!

    All our customers can enjoy a better visualization with this enhancement of standardization on our platform.\




    <figure><img src="../.gitbook/assets/image (450).png" alt="" width="188"><figcaption></figcaption></figure>

## Release 10.0.18 - November 2023

* **Ability to search by source-key** in the Source Overview & Destination Overview UIs:&#x20;

<figure><img src="../.gitbook/assets/image (436).png" alt=""><figcaption></figcaption></figure>

*   **New version of the Source Data Quality** UI: It's even easier to see the quality of your data at a glance ! \
    "_What proportion of events have errors to need to be fixed?_" The new Overview chart give you the answer in realtime.\
    You will also be able to filter by environment (by default Production environment is shown) and by source.\


    <figure><img src="../.gitbook/assets/image (435) (1).png" alt=""><figcaption></figcaption></figure>
* **Platform**
  * User Management UI: speed increase x3 \

*   **Destinations**

    * GEC destination enhancement: Avoid random "failed\_get\_conversion\_id" errors in Event Delivery.&#x20;


* **Mobile**
  * **React-Native:**&#x20;
    * add `useLegacyUniqueIDForConsentID` &  `useLegacyUniqueIDForAnonymousID` &#x20;
    *   startScreen for privacy center choose your launch on the Vendors or Purposes UI

        \

* **Documentation**
  * [Easy setup guide for Privacy in GTM](https://doc.commandersact.com/features/consent-management/setup-guides/tag-manager/google-tag-manager-gtm)
  * [Data retention duration](https://doc.commandersact.com/configure/data-management/data-retention-duration)

## Release 10.0.17 - 24/10/23

* **Platform**
  * Security enhancement : passwords now required a minimum of 12 characters
  * Proxy configuration (Cloud Flare, etc.) in domain management UI

<figure><img src="../.gitbook/assets/image (430) (1).png" alt=""><figcaption></figcaption></figure>

* **TMS/CMP interfaces:**&#x20;
  * Slightly increase UI loading time on TMS pages​
  * UI random errors fixed\

*   **Server Side**

    * **Event Inspector** UX improvement: user properties (standard and custom) are now searchable by default



    <figure><img src="../.gitbook/assets/image (431).png" alt=""><figcaption></figcaption></figure>

    * **Destination Event delivery** UX improvement:​ Longer duration for conservation of error details​

    <figure><img src="../.gitbook/assets/image (432).png" alt=""><figcaption></figcaption></figure>

    * **Destination Properties Transformations** option UX improvement: allows the same transformations as the Data Cleansing UI​

    <figure><img src="../.gitbook/assets/image (433).png" alt=""><figcaption></figcaption></figure>


* **Debug Mode for Source/Destination Live Event Inspector** \
  Adding a special parameter to you events allows you to have them visible in Event Inspector, even on production environment with billions of events. This debug parameter will allows you to bypass the "Intelligent Sampling". \
  [https://doc.commandersact.com/features/sources/live-event-inspector#debug-mode](https://doc.commandersact.com/features/sources/live-event-inspector#debug-mode)\

* **Mobile**
  *   **Consent​**

      Android & iOS: ​

      * iAB new function to get the number of IAB vendors​
        * iAB remove consentOutdated callback migrating to iabv2.2​

      Android:  do\_not\_track parameter as a boolean inside the payload​

      IOS: illustrations fix on privacy center​

      ​
  *   **Core​**

      * Android & iOS: translations fix on migrating to iab v2.2​


  *   **Server Side​**

      * Android & iOS: ​
        * language and country code from the device​
        * 2 function to use legacy ID TC\_UNIQUEID​

      ​
*   **New destinations**

    * The Trade Desk: CAPI
    * Piwik PRO
    * Alphalyr Marketing Studio
    * TradeTracker


* **Destinations​ updates**
  * Awin: support for “Smart Mapping” and “Custom Event Properties”.​
  * Mapp: support for "Independent parameters“.



## Release 10.0.16 - 24/09/23

* **TMS/CMP ​interfaces:** Add a loading indicator to TMS/CMP interfaces\

* **Copy Manager​**: When you duplicate a site (aka workspace), you can now copy Server Side configurations (PlatformX    activation, Sources, Destinations, Data Management, Enrichments, etc...)

<figure><img src="../.gitbook/assets/image (425).png" alt=""><figcaption></figcaption></figure>

*   **Interface speed improvements​** on the following pages:

    * TMS: Container overview => +22%​
    * TMS: External variable => +41%​
    * Mix: Attribution option => + 46%​
    * CMP: Privacy banners overview => +38%​
    * Admin: Profile management => +21%
    * Segment overview => +40%


* **Files imports:** The fields mapping now support conditionnal value transformation with [Data cleansing formulas​](../features/data-quality/data-cleansing/supported-transformation-functions/)\

*   **Data Activation: Variables** **UI** can now be reached from Segment overview\


    <figure><img src="../.gitbook/assets/image (428).png" alt=""><figcaption></figcaption></figure>
* **Mobile​**\
  Android & iOS: add language & region​\
  Android & iOS: Firebase Destination (for Analytics)​\
  IOS: Fix for non-IAB Privacy​\

* **Destinations​ updates**
  * Adobe Analytics​ authentication token. You can see our [updated documentation here](https://doc.commandersact.com/features/destinations/destinations-catalog/adobe/adobe-analytics)
  * Pinterest: support for "click\_id“ and "view\_item" mapped to "page\_visit“.​
  * Piano Analytics Collection API: removed useless “ref” parameter.​

## Release 10.0.15 - 24/08/23



* **New API "Users Activities logs"**\
  This new API allows administrators to get all users activities history (who has changed what, when, etc...). Read the technical [API documentation](https://commandersact.github.io/api\_doc/#tag/AdminActivityLogs) to start using it.\

*   **Live Report Builder: enhancement on UI**\
    The filters are now directly visible as before, and the data set limitation (if any) is visible on mouse over only on the flag "limited dataset"

    \


    <figure><img src="../.gitbook/assets/image (421).png" alt=""><figcaption></figcaption></figure>
*   **Data Cleansing: new function  "GET(property\_name)"**\
    Allows to work on a property name that contains special characters incompatible with formula. For example if your property name contains a `-` like `page-count` you will not be able to write this formula because it is interpreted as a minus sign :\


    ```
    page-count-5
    ```

    Now you can, just write :\


    ```
    GET("page-count")-5
    ```

    \
    You can read our dedicated [documentation here](https://doc.commandersact.com/features/data-quality/data-cleansing/supported-transformation-functions)\

*   **Consent dashboards: new metric for "Global Privacy Control"**\
    This new metric will help you to identify the amount of "Optout All" registered through a GPC parameter turned ON\


    <figure><img src="../.gitbook/assets/image (422).png" alt=""><figcaption></figcaption></figure>
* **Consent banners: IAB TCF v2.2 compliance**\
  Our customers can now be compliant with the latest framework of IAB TCF (v2.2)\
  It is available for Web & Mobile apps !\
  If you need more information about migration please check [this section of our documentation](https://doc.commandersact.com/features/consent-management/knowledge-base/iab-tcf-v2.2-release-details)\

* New destination : [Google Ads Conversion Adjustment](../features/destinations/destinations-catalog/google/google-conversion-adjustments.md) (_closed beta_)\

* Normalized Datalayer (closed beta)_:_ Add an option to not consider missing properties as an issue (not impacting quality score). Accept unspecified properties without warning\

* UX enhancements and speed up of Destination's interfaces (destination list, etc.)



## Release 10.0.14 - 24/07/23



*   **Performance tab of Facebook CAPI destinations**\
    For more information, you can have look to our new documentation's [dedicated page](https://doc.commandersact.com/features/destinations/destinations-catalog/facebook/facebook-conversions-api/performance-tab-event-match-quality)\


    <figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>



*   **Live Report Builder: 2 new charts**\
    We added two new type of charts in LRB : bar chart and pie chart. \
    You can retrieve them in the edition part of a LRB report !\


    <figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



*   **Live Report Builder: UX enhancement**\
    The filters are now directly visible as before, and the data set limitation (if any) is visible on mouse over only on the flag "limited dataset"\


    <figure><img src="../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



* **Mobile: New SDK version released for IAB TCFv2.2**\
  For more details, please read our [documentation page](https://community.commandersact.com/consent-management/knowledge-base/iab-tcf-v2.2-release-details/iab-tcf-v2.2-migration-guide-app)\
  For technical instructions, you can refer to our Github : [Android](https://github.com/CommandersAct/AndroidV5/tree/master/TCIAB) &[ IOS](https://github.com/CommandersAct/iOSV5/tree/master/TCIAB)

## Release 10.0.13 - 24/06/23

* **New Source: Pixel Tracking API**\
  Pixel Tracking API, also known as 1x1 gifs, or clear gifs, allows you to send data to Commanders Act with a HTTP GET request from your server, your local console or any development framework. \
  You can have a look to [our dedicated documentation](https://doc.commandersact.com/features/sources/sources-catalog/web/pixel-tracking) page for more details.\
  \
  ![](<../.gitbook/assets/image (1) (8).png>)\

*   **Data Cleansing: New functions available**\
    9 new functions related to dates: \
    DATEPARSE ; DATEFORMAT ; DATEADD ; DATESUB ; DATEDIFF ; AGE ; \[YEAR, MONTH, DAY, HOUR, MINUTES, SECONDS] ; TIMEZONE ; TODAY\
    \


    <figure><img src="../.gitbook/assets/image (10) (1) (2).png" alt="" width="563"><figcaption></figcaption></figure>
*   **Consent: New setting "Global Privacy Control"**\
    Setting to be configured at the banner level. Required for CCPA banners\
    For further information, you can read [this page](https://community.commandersact.com/consent-management/knowledge-base/ccpa-and-global-privacy-control)\


    <figure><img src="../.gitbook/assets/image (3) (1) (1) (2) (1).png" alt="" width="485"><figcaption></figcaption></figure>


*   **Destinations: New section 'events filtered' on Event Delivery tab**\
    For all destinations, on Event Delivery tab, there is a new section with number of filtered events (consents, conditions defined)\


    <figure><img src="../.gitbook/assets/image (4) (1) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>
*   **Destinations: Dry Mode (lab) - Closed Beta**\
    The Dry mode allows you to simulate sending events, **but events are not sent** to the destination.\


    <figure><img src="../.gitbook/assets/image (2) (6).png" alt=""><figcaption></figcaption></figure>
*   **Destinations: update on Facebook Conversion API**\
    We released a Performance tab with Event Match Quality score\
    The Performance tab can now display Event Match Quality insights, coming from Facebook. \
    It represents the matching quality, referring to the quality of events sent (completeness of data, like events with email, phone, fbp, fbc...). More identifiers are present on events sent, better is the score.\
    You can have a look to our [documentation ](https://doc.commandersact.com/features/destinations/destinations-catalog/facebook/facebook-conversions-api/performance-tab-event-match-quality)\


    <figure><img src="../.gitbook/assets/image (5) (3) (1) (1).png" alt=""><figcaption></figcaption></figure>


*   **UI Improvements: Statistics on weather icons**\
    On hover of weather icons, you can see the percentage of accepted/refused events\


    <figure><img src="../.gitbook/assets/image (6) (4) (1).png" alt=""><figcaption></figcaption></figure>





## Release 10.0.12 - 24/05/23

*   **Event delivery improvement for Audience based destinations**\
    Event Delivery errors messages for Audience connectors (API connectors such as Facebook Custom Audience, Google Customer Match...)  now provide more detailed information about errors encountered.

    <figure><img src="../.gitbook/assets/image (2) (1) (2).png" alt=""><figcaption></figcaption></figure>
*   **Sources: update on GTM Bridge**\
    A Commanders Act source key is now required in the bridge configuration. As, in the future, events without a source key will be discarded, it is important that you apply the update.\
    If it is not already done, please update it as soon as you can, following the instructions available in our [documentation](https://doc.commandersact.com/features/sources/sources-catalog/gtm).\
    \


    <figure><img src="../.gitbook/assets/image (15) (4).png" alt=""><figcaption></figcaption></figure>


*   **Destinations settings enhancement:**\
    New dynamic text input component on settings fields (except Smart Mapping for the moment)\
    \


    <figure><img src="../.gitbook/assets/image (10) (5).png" alt=""><figcaption></figcaption></figure>
* **Mobile:**&#x20;
  * **Video Events are now natively supported**\
    For more informations about video events, you can have a look to [our documentation](https://doc.commandersact.com/developers/tracking/about-events/mobile-sdk-event-specificity)
  * **the property 'do not track' has been added**\
    Required by CNIL for Consent Statistics exempted. For more information check [our documentation](https://community.commandersact.com/consent-management/knowledge-base/consent-cookies-exemption/implementation-guide-for-exempted-consent-statistics-fr-market)
  * &#x20;**Flutter SDK minor updates**\

*   **New destinations releases:**\
    \
    [**Adform**](../features/destinations/destinations-catalog/adform.md)**:**\


    <figure><img src="../.gitbook/assets/image (4) (5).png" alt="" width="226"><figcaption></figcaption></figure>
*   **Destinations updates:**\
    \
    **Equativ:** improvements and user/cookie sync fix\


    <figure><img src="../.gitbook/assets/image (14) (3).png" alt="" width="230"><figcaption></figcaption></figure>

    **GA4:** send all properties option, automatic session id. \
    Proxy mode is open to more beta customers. Global opening on 25/05\


    <figure><img src="../.gitbook/assets/image (18) (4).png" alt="" width="227"><figcaption></figcaption></figure>

    **Piano Analytics:** send all properties\


    <figure><img src="../.gitbook/assets/image (8) (5).png" alt="" width="241"><figcaption></figcaption></figure>

    **TikTok:** “Smart Mapping” support\


    <figure><img src="../.gitbook/assets/image (1) (1) (2) (1).png" alt="" width="227"><figcaption></figcaption></figure>

    **Partnerize:** field encoding fixes\


    <figure><img src="../.gitbook/assets/image (11) (2).png" alt="" width="229"><figcaption></figcaption></figure>

    **Awin:** dynamic fields support

    <figure><img src="../.gitbook/assets/image (12) (5).png" alt="" width="230"><figcaption></figcaption></figure>

    \
    **Commission Junction:** dynamic fields support

    <figure><img src="../.gitbook/assets/image (6) (4).png" alt="" width="230"><figcaption></figcaption></figure>



## Release 10.0.11 - 24/04/23

*   **A new item has been added to the navigation menu of our platform: 'Data Governance'**. \
    For the moment, you will find the pages related to your privacy banners configuration's in the tab 'Consent Management'. \
    More pages are coming soon!

    <figure><img src="../.gitbook/assets/image (10) (1).png" alt="" width="181"><figcaption></figcaption></figure>
*   **Data Cleansing: 2 new function for your formulas:**\


    <figure><img src="../.gitbook/assets/image (108).png" alt="" width="422"><figcaption></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (93).png" alt="" width="419"><figcaption></figcaption></figure>
*   **New destinations releases**\
    \
    **Data Activation Legacy:** Only for Data Activation customers. Gives you the possibility to map the format of the events to the format of the data activation (Data Commander variables). To go deeper, you can consult our [online documentation](https://doc.commandersact.com/features/destinations/destinations-catalog/data-activation-legacy) \


    <figure><img src="../.gitbook/assets/image (105) (1).png" alt=""><figcaption></figcaption></figure>

    **GA4 Proxy Mode:** The proxy mode option allows you to anonymize data before to send it to Google.\
    \*We also added analyses, suggestions and report's impact in our [online documentation](https://doc.commandersact.com/features/destinations/destinations-catalog/google/google-analytics-4/google-analytics-4-proxy-mode#3.-impact-analysis-and-open-suggestions)\
    \


    <figure><img src="../.gitbook/assets/image (107) (1).png" alt=""><figcaption></figcaption></figure>
*   **Destinations updates**\
    \
    **GA4:** Send all properties in one click to Google\


    <figure><img src="../.gitbook/assets/image (106).png" alt="" width="308"><figcaption></figcaption></figure>

    \
    \
    **TikTok:** Offers a smart mapping option

<figure><img src="../.gitbook/assets/image (84) (1).png" alt=""><figcaption></figcaption></figure>

* **Bridge updates**\
  \
  GTM bridge: a Commanders Act source key is now required in the bridge configuration. As, in the future, events without a source key will be discarded, it is important that you apply the update.\
  For further information, read the bridge’s [updated documentation](https://doc.commandersact.com/features/sources/sources-catalog/gtm).

## Release 10.0.10 - 24/03/23

* **Formula component enhancement (Data Cleansing, Event Enrichment, ...)**\
  The field now resizes automatically according to the size of the formula, to facilitate the reading and writing of complex formulas. Users can also resize the field themselves if needed

<figure><img src="../.gitbook/assets/image (9) (3) (1).png" alt=""><figcaption></figcaption></figure>

* **New User Rights**\
  3 new user rights have been added in Rights management interface to manage the _Destination Builder_ feature

<figure><img src="../.gitbook/assets/image (3) (4).png" alt=""><figcaption></figcaption></figure>

* **New SDKs:** \
  \
  SDK for **Flutter** is launched\
  For further informations, please check our github\
  [https://github.com/CommandersAct/tcserverside-plugin  \
  https://github.com/CommandersAct/tc-consent-plugin  \
  https://github.com/CommandersAct/TCMobileDemo-flutter](https://github.com/CommandersAct/tcserverside-pluginhttps://github.com/CommandersAct/tc-consent-pluginhttps://github.com/CommandersAct/TCMobileDemo-flutter)\
  \
  SDK **Angular 15** is available\
  Note : it's also compatible with Angular 14.\
  Check our GitHub for more informations :\
  [https://github.com/CommandersAct/ngx-tag-commander](https://github.com/CommandersAct/ngx-tag-commander)\
  [https://github.com/CommandersAct/ngx-tag-commander/blob/master/README.md](https://github.com/CommandersAct/ngx-tag-commander/blob/master/README.md)\

*   **Filters enhanced on destinations**&#x20;

    * quick/easy filter with autocomplete
    * more operators (contains, match regex, etc.)
    * advanced mode with formula (ability to create very complexe filter, applying our formula function to any condition)\


    <figure><img src="../.gitbook/assets/filtersv2-demo.gif" alt=""><figcaption></figcaption></figure>
*   **Data Quality indicators and trend graph are now displayed on all sources**\


    <figure><img src="../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>
*   **New option on LRB report** \
    you can now choose to do not display the "non attributed" line in a report



    <figure><img src="../.gitbook/assets/image (5) (1) (4).png" alt=""><figcaption></figcaption></figure>
* **New destinations releases**\
  \
  **Partenerize** \
  Note : this destination allows a dynamic field\
  <img src="../.gitbook/assets/image (7) (3) (1).png" alt="" data-size="original">\
  \
  **SmartAd Server**\
  ![](<../.gitbook/assets/image (12) (3).png>)\
  \
  **Rakuten Events**\
  ![](<../.gitbook/assets/image (15) (1).png>)\

* **Destinations updates**\
  \
  **Mapp:** usability improvements\
  ![](<../.gitbook/assets/image (26) (1).png>)\
  \
  **Partnerize:** Advanced operations added\
  ![](<../.gitbook/assets/image (16).png>)\
  \
  **Snapchat:** SmartMapping support\
  ![](<../.gitbook/assets/image (24) (1).png>)





## Release 10.0.9.1 - 22/02/23

* **Destination builder - Javascript sandbox**\
  Create your own custom destination using basic javascript code !\
  You can create event-based or audience-based destination.\
  ![](<../.gitbook/assets/image (20).png>)![](<../.gitbook/assets/image (23).png>)![](<../.gitbook/assets/image (1) (3) (3).png>)![](<../.gitbook/assets/image (21).png>)

\
More information here:

{% content-ref url="../features/destinations/destination-builder/" %}
[destination-builder](../features/destinations/destination-builder/)
{% endcontent-ref %}

* **UI enhancement**\
  Data Cleansing and Event Enrichment features benefit for a even more userfriendly autocomplete property selector component. Find quicly your property or create a new one in a click.\
  ![](<../.gitbook/assets/image (18) (3).png>)
*   **Data Cleansing – new functions added​**

    [JSON\_PARSE() and VALUE\_FROM\_JSON()​](../features/data-quality/data-cleansing/supported-transformation-functions/#available-functions)
*   **Events reference update**

    [video events](../developers/tracking/events-reference/video-event-reference.md) has been added
* **New destinations:**&#x20;
  * [Pinterest](../features/destinations/destinations-catalog/pinterest.md)
  * [Equativ ](../features/destinations/destinations-catalog/equativ-audience.md)(audience)
  * [Partnerize](../features/destinations/destinations-catalog/partnerize.md)
  * Updates: Matomo, Kwanko, Google Universal Analytics
* **Consent management -  Exempted statistics** ​
  * New tag in the library to facilitate the setup​
* **Event Replay -**  _Closed alpha​_
* **New source:**&#x20;
  * **Flutter - for mobile App** – _Closed beta_​
* **Campaign analysis ​**
  * Campaign Overlap enhanced => possibility to go back up to 30 days​\
    ![](<../.gitbook/assets/image (18).png>)
  * Make it possible to send a timestamp with the incoming hit​ of your campaigns collection

## Release 10.0.9 - 14/02/23

* **27% increase in the speed** of the interfaces listed below:
  * Client-side TMS UIs
  * Segments UIs
  * Admin UIs
  * Campaign options UIs
  * Banner builder and consent Dashboard UIs

## Release 10.0.8 - 24/01/23

* **Product enrichment** & **External API -** _Public opening_\
  Enrich your events in real time with data transmission from your product catalog or from an external API. It does not requires any data storage \
  ![](<../.gitbook/assets/image (3) (2) (1).png>)\

*   **OnSite API:**

    [5 new commands](https://community.commandersact.com/consent-management/onsite-api/consent.onready) are available, to help you on consent behaviour management:&#x20;

    * cact('consent.onReady', (consent) => console.log(consent))
    * cact('consentBanner.show')
    * cact('consentBanner.hide')
    * cact('consentCenter.show')
    * cact('consentCenter.hide')


* **Destinations:**
  * **Adobe Analytics**: beta
  * **Pinterest**: beta
  * **Piano Analytics**: improvement you can now set the Piano Site Id parameter with a dynamic value

## Release 10.0.7 - 24/12/22

* **Event enrichment** – **External API** Version 1.0 closed alpha. _Public opening on 12 Jan._\
  Enrich your events with instantaneous data transmission from an external API - no data storage required\
  ![](<../.gitbook/assets/image (10) (3) (1).png>)
* **Destinations:**
  *   Easier debug in Event delivery and Event inspector, now both shows information when a javascript error raise in the destination code. Usefull when you build your own destination using the [Destination builder's Javascript Sandbox](../features/destinations/destination-builder/):

      <figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>
  * **Google Universal Analytics** (GA3): beta
  * **Adobe Analytics**: closed beta
  * **Audience based destinations :** All "closed beta" or "closed alpha" destinations are now open to everybody.\
    Also, all these audience-based destinations benefit from the [Event Delivery](../features/destinations/event-delivery.md) feature and Threshold [Alerting](../features/destinations/event-delivery.md#alerting) feature\\
*   **Explore:** Enhancement of LRB integrations in the platform\\

    <figure><img src="../.gitbook/assets/image (3) (1) (4).png" alt=""><figcaption></figcaption></figure>

## Release 10.0.6 - 24/11/22

* Data Management – New feature:​
  * **Data Cleansing** no-code : **Rename event** public opening.\
    ​![](<../.gitbook/assets/image (1) (3) (1).png>)
  * **Campaign analytics** interfaces: public opening
  * **Event collection** UI : add a **global counter​**\
    ![](<../.gitbook/assets/image (2) (2) (2).png>)
* **Event enrichment** – **product catalog** enhancement (closed alpha)​ _Public opening on 12 Jan._\
  ![](<../.gitbook/assets/image (3) (5).png>)
* Destinations:​
  * Destination builder **Sandbox JS**: Closed alpha\
    ![](<../.gitbook/assets/image (6) (3).png>)
  * **Google Enhanced Conversion** connector now supports more events​
  * **Commission Junction** : smart mapping adjustments and public opening​
  * **Google Univers Analytics**: closed beta
  * **Partnerize**: closed alpha
  * **TikTok**: Add **Smart Mapping** : closed alpha
  * **Adobe Analytics** : closed alpha
* Global Platform X:​
  * **Even faster interfaces** on : CMP UI, client-side TMS UI, Administrations UI, Campaigns Analytics UI => closed alpha. _Public opening on 13 Jan._
  * **Data Activation** features: public opening

## Release 10.0.5 - 24/10/22

* **Data management - new feature:**
  * [**Data Cleansing**](../features/data-quality/data-cleansing/) **no-code :** Clean, fix, refine your event data with a userfriendly interface (closed beta) _Public opening on 21 Nov._\
    <img src="../.gitbook/assets/image (2) (5).png" alt="" data-size="original">![](<../.gitbook/assets/image (1) (6) (1).png>)
* **Enrichment - new feature:**
  *   **Event enrichment from your Product catalog:** Copy in realtime time any properties of your imported product catalog to your choosen event.\
      Use case example: send a purchase event with only product ids and enrich your events on the server with all the product properties you have in your product catalog for these ids.\
      (closed beta) _Public opening on 08 Dec._\\

      ***

      <figure><img src="../.gitbook/assets/image (4) (2) (2).png" alt=""><figcaption></figcaption></figure>
*   **Destinations improvements:**

    * New destinations: [Commission Junction](../features/destinations/destinations-catalog/commission-junction.md) (closed alpha), Partenerize (closed alpha),[ Google Customer Match](../features/destinations/destinations-catalog/google/google-customer-match.md) (public beta)
    * New feature : **smart mapping** (closed alpha) : visualize/edit the data mapping done automatically by the system between your event properties and the destination's API.\
      _This feature will be progressively open on each destination during next months._\\

    <figure><img src="../.gitbook/assets/image (18) (2) (1).png" alt=""><figcaption></figcaption></figure>

    * Enhancement on existing destinations: Tradedoubler, Criteo conversion, Snapchat, GEC, TikTok, Kwanko
    * Event delivery: error's labels enhancement, easier to understand what is wrong
* **Sources enhancements:**
  * Web container : Add a summary/setup guide step.
* **Campaign analytics - new feature:**
  * New **whitelist** feature for landing page redirections (closed beta)

## Release 10.0.4 - 24/09/22

* **Global Platform enhancement**:
  * Help icon: a new menu that allows you to quickly find helps or send feedbacks\
    ![](<../.gitbook/assets/image (7) (2) (3).png>)
  * **Onboarding tour:**\
    Interactive tutorials have been added to discover the platform features. You can access to it through the help icon at the top right\
    <img src="../.gitbook/assets/image (1) (4) (2) (1) (1) (1) (1) (1) (1) (2).png" alt="" data-size="original">
* **Source improvements:**
  * Trend graph and quality indicator for HTTP Tracking API sources.\
    ![](<../.gitbook/assets/image (5) (1) (3).png>)
  * Quality indicators have also been added to Source Data Quality view. For each event you can now see at a glance if an event has a quality issue.\
    <img src="../.gitbook/assets/image (1) (6).png" alt="" data-size="original">
  * iOS SDK: Core 5.1.1 ServerSide 5.1.2
    * Supporting TVOS Consent 5.1.2
    * Disclosure for IAB's vendors
* **Destinations improvements:**
  * Event delivery detail popin now shows also the intial events beside the destination hit and response. It allows to easily understand if there is wrong or missing properties in the original event\
    <img src="../.gitbook/assets/image (8) (1) (2).png" alt="" data-size="original">
  * Event inspector now show initial event too in each log
  * Enhancement on existing destinations : Piano Analytics
* Explore improvements:
  * Live report builder: you can now change in live the attribution model without having to edit the report\
    ![](<../.gitbook/assets/image (9) (2).png>)

## Release 10.0.3 - 24/08/22

* Sources improvements:
  * Live Events Inspector for sources, available both in Sources menu (for all sources) and on each source (tab Event Inspector). It allows to inspect/debug your incoming events​
* Destinations improvements: ​
  * _Advanced mapping_ feature evolves to Event [_Properties transformation_](../features/destinations/advanced-mapping.md) feature.
    * Ability to create new property and map them to existing one for a specific destination
    * Ability to remove event properties for a specific destination\
      ![](<../.gitbook/assets/image (2) (3) (1) (1).png>)
  * [_Alerting_ ](../features/destinations/event-delivery.md): _Event delivery_ alerting is now open to everybody on channels _email_, _Slack_ and _Microsoft Teams_.\
    Be alerted in real-time when one of your destination delivery drop below your threshold.\
    ![](<../.gitbook/assets/image (25).png>)\\
  * Enhancement on existing destinations : Piano Analytics, Snapchat and Google Enhanced conversions
  * [Webhook ](../features/destinations/destinations-catalog/webhook.md)enhancement : ability to use properties, static values, or a melt of both, everywhere (url, body, headers)​
  * New destinations :
    * [Matomo](../features/destinations/destinations-catalog/matomo.md)
    * [Mapp](../features/destinations/destinations-catalog/mapp.md)
  * Template importer (closed alpha) : import in the destination catalog your custom destination template build with the [sandbox JS](../features/destinations/destination-builder/javascript-destination-builder/)\
    (Compatible with GTM templates)
* Campaign analysis -> Live Report builder look and feel enhancements
* Minor UI enhancements:
  * tooltip on all destinations or sources logo in overview UI
  * Increase clarity of labels on some UI
  * Add technical base for future onboarding features

## Release 10.0.2 - 24/07/22

* Event collection​\
  ![](<../.gitbook/assets/image (15) (1) (1).png>)\
  Follow your events arriving at the platform in near-realtime, understand which source send it and which destinations are using it.​\
  Analyze past event count, up to one year ago, to master your event collection and associated cost\\
*   Sources improvements: ​

    * Duplicate a source (except web containers)​
    * Link/unlink destinations to a source (create and edit)​

    ![](<../.gitbook/assets/image (20) (1).png>)
* Destinations improvements: ​
  * Duplicate a destination to edit it in another environment​
  * Activate/ deactivate switch​, to pause a destination
  * Userfriendly way to select a specific sources to a destination (create and edit)​
  * Advanced mapping​ on each destination
  * TikTok connector (Web mode only, App mode in September)​
  * Piano Analytics, Snapchat, Criteo, GA4 enhancements/fix​
  * Matomo Analytics in closed alpha test\
    ![](<../.gitbook/assets/image (19) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)![](<../.gitbook/assets/image (1) (5).png>)

## Release 10.0.1 - 24/06/22

* Sources improvements: ​
  * Source data quality in health menu (global) and in a tab for each source​
  * Adding new sources, currently in closed alpha (Shopify, pixel tracking, cost imports…)​
  * Source event inspector : inspect each event individually (intelligent sampling)
  * Adding new environment: ‘development’​
* Destinations improvements: ​
  * Consent categories dropdown on destination’s filters​​
  * Destination description: what you will need & supported sources sections​
  * Adding new environment: ‘development’​
* Improvements on 2FA​
* Integration of segment stats interface​
* New connectors: Criteo Events, Tradedoubler, Xandr\*, Appnexus\*, Tableau\*​
* Destination enhancements:​
  * Webhook v2 (more methods, and more formatting data possibilities)​
  * Google Enhanced Conversion v2 (new Google API)​
  * Google Analytics 4 (more options)​
  * AT Internet (cookie server)​
  * Awin (more advanced affiliation property option)

(\*) audience based destination

## Release 10.0.0 - 21/01/2022

* Serverside v2 interfaces - closed beta 1

## Release 0.0.12 - 01/02/1970

* Removed humans, they weren't doing fine with animals.
* Animals are now super cute, all of them.

## Release 0.0.1 - 01/01/1970

* Introduced animals into the world, we believe they're going to be a neat addition.
