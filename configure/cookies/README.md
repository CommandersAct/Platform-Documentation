---
description: An overview of cookies used by the Commanders Act platform.
---

# Cookies

{% hint style="warning" %}
The technical session cookies for First party domain tracking have been renamed. ("PHOENIX" replaced by "FIRST" in the cookie name) - 06/05/2024 16:01
{% endhint %}

## Predefined Cookies <a href="#predefined-cookies" id="predefined-cookies"></a>

Following cookies are used automatically in depending on the installed Commanders Act products.

### TMS + CMP + CAMPAIGN + DATA&#x20;

<details>

<summary>CAID</summary>

**Product(s) related:** CAMPAIGN + DATA+ TMS + CMP

**Type:** Cookie

**Domain:** domainfirstClient

**Lifetime:** 365 days

**Value:** Commanders Act users ID

**Owner:** Commanders Act

**Storage purpose(s):** The CAID is the user identifier for cookie 1st

</details>

<details>

<summary>TCID</summary>

**Product(s) related:** CAMPAIGN + DATA+ TMS + CMP

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** 365 days

**Value:** Commanders Act ID.

**Owner:** Commanders Act

**Storage purpose(s):** Visitor identifier used to compute deduplicated statistics per user (for campaign and on-site tracking, segmentation, ...). 

</details>

<details>

<summary>WID</summary>

**Product(s) related:** DATA + TMS + CMP + CAMPAIGN

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** Session

**Value:** DataCommander session ID.

**Owner:** Commanders Act

**Storage purpose(s):** Used to identify when the browser is closed in order to split page views into multiple functional sessions.

</details>

<details>

<summary>tC_Sync</summary>

**Product(s) related:** CAMPAIGN + DATA+ TMS + CMP

**Type:** Local Storage

**Domain:** /

**Lifetime:** /

**Value:** Timestamp.

**Owner:** Commanders Act

**Storage purpose(s):** Technical cookie that is used to store the timestamp of the last cookie sync that was performed for this user agent. A cookie sync matches the visitor ID of Commanders Act solutions (TCID) with the visitor ID of other solutions. Cookie sync is optional and can be deactivated by Commanders Act users via the Commanders Act support. (cookie exempted)

</details>

### TMS

<details>

<summary>tc_sample_{idsite}_{idrule}</summary>

**Product(s) related:** TMS

**Type:** Cookie

**Domain:** Customer domain

**Lifetime:** Session

**Value:** TMS sampling done in the container rules.

**Owner:** Commanders Act

**Storage purpose(s):** Used for visitor and session sampling in the TMSCommander rules.

</details>

<details>

<summary>TCREDIRECT_DEDUP</summary>

**Product(s) related:** TMS

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** Session

**Value:** CAMPAIGN redirect flag (used for deduplication).

**Owner:** Commanders Act

**Storage purpose(s):** Used when the deduplication is based on CAMPAIGN tracking (so the CAMPAIGN tracking is taken into account and not the landing page tracking)

</details>

<details>

<summary>TC_CHECK_COOKIES_SUPPORT</summary>

**Product(s) related:** TMS

**Type:** Cookie

**Domain:** Customer domain

**Lifetime:** Session

**Value:** 1 if true

**Owner:** Commanders Act

**Storage purpose(s):** Technical cookie, TMS verification of Cookies deposit (exempted)

</details>

### CMP

<details>

<summary>TCPID</summary>

**Product(s) related:** CMP (v1 & v2)

**Type:** Cookie

**Domain:** Customer domain

**Lifetime:** 365 days

**Value:** CMP Commander ID.

**Owner:** Commanders Act

**Storage purpose(s):** Used to identify visitors exposed to the privacy banner. CMP Commanders Act uses this cookie to measure statistics for privacy banner usage until visitors provide consent for the TCID cookie. With this 2-cookie system, CMP Commanders Act is the only CMP that has been granted the right of exemption from consent for statistical measurement by the French CNIL. [https://www.cnil.fr/fr/solutions-pour-les-cookies-de-mesure-daudience](https://www.cnil.fr/fr/solutions-pour-les-cookies-de-mesure-daudience) \
\
\*Cookie exempted by CNIL\


</details>

<details>

<summary>TC_PRIVACY (default)</summary>

**Product(s) related:** CMP V2

**Type:** Cookie

**Domain:** Customer domain (default, can be customized)

**Lifetime:** 396 days

**Value:** Privacy optin/optout user, privacy version and optin categories.

**Owner:** Commanders Act

**Storage purpose(s):** Used for user status storage (optin or optout) and Privacy banner display.\
\
\*Cookie exempted by CNIL\


</details>

<details>

<summary>TC_PRIVACY_CENTER (default)</summary>

**Product(s) related:** CMP V2

**Type:** Cookie

**Domain:** Customer domain (default, can be customized)

**Lifetime:** 396 days

**Value:** Privacy optin categories.

**Owner:** Commanders Act

**Storage purpose(s):** Used to display the optin/optout categories in the Privacy Center if the user re-open it.\
\
\*Cookie exempted by CNIL\


</details>

<details>

<summary>tc_test_cookie</summary>

**Product(s) related:** CMP V2

**Type:** Cookie

**Domain:** Customer domain (default, can be customized)

**Lifetime:** 396 days

**Value:** Banner display

**Owner:** Commanders Act

**Storage purpose(s):** Cookie linked to the display of the privacy banner, it allows to check whether cookies can be deposited and not to redisplay the consent banner when consent is given. Deposited then disappears, cannot be deleted. Technical cookie (exempted)\


</details>

<details>

<summary>TC_PRIVACY_IAB_VENDORLIST</summary>

**Product(s) related:** CMP V2

**Type:** Local Storage

**Domain:** Customer domain (default, can be customized)

**Lifetime:** /

**Value:** IAB Global Vendor List

**Owner:** Commanders Act

**Storage purpose(s):** Used to cache the IAB TCF Global Vendor List to optimise the response time of the IAB TCF consent API.

</details>

<details>

<summary>TC_PRIVACY_TCF</summary>

**Product(s) related:** CMP V2

**Type:** Local Storage

**Domain:** Customer domain (default, can be customized)

**Lifetime:** /

**Value:** IAB Global Vendor List

**Owner:** Commanders Act

**Storage purpose(s):** Used to cache the IAB TCF Consent API Response to optimise the response time of the API.

</details>

<details>

<summary>TC_OPTOUT (deprecated CMP version 1)</summary>

**Product(s) related:** CMP V1 (Previous Privacy)

**Type:** Cookie

**Domain:** Customer domain (default, can be customized)

**Lifetime:** 396 days

**Value:** Privacy: optin/optout user, privacy version and optin categories.

**Owner:** Commanders Act

**Storage purpose(s):** Used for user status storage (optin or optout) and Privacy banner display. \
\
\*Cookie exempted by CNIL\


</details>

<details>

<summary>TC_OPTOUT_categories (deprecated CMP version 1)</summary>

**Product(s) related:** CMP V1 (Previous Privacy)

**Type:** Cookie

**Domain:** Customer domain (default, can be customized)

**Lifetime:** 396 days

**Value:** Privacy optin categories.

**Owner:** Commanders Act

**Storage purpose(s):** Used to display the optin/optout categories in the Privacy Center if the user re-open it. \
\
\*Cookie exempted by CNIL\


</details>

### CAMPAIGN + TMS (deduplication)

<details>

<summary>tc_cj_v2</summary>

**Product(s) related:** CAMPAIGN + TMS

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** 365 days

**Value:** Deduplication CJ storage ("\&chn=" and "\&src=" parameters)

**Owner:** Commanders Act

**Storage purpose(s):** Used for user customer journey storage for TMS deduplication (channel and source storage).

</details>

<details>

<summary>tc_cj_v2_cmp</summary>

**Product(s) related:** CAMPAIGN + TMS

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** 365 days

**Value:** Deduplication CJ storage ("\&chn=" and "\&src=" parameters)

**Owner:** Commanders Act

**Storage purpose(s):** Used for user customer journey storage for TMS deduplication (campaign storage).

</details>

<details>

<summary>tc_cj_v2_med</summary>

**Product(s) related:** CAMPAIGN + TMS

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** 365 days

**Value:** Deduplication CJ storage ("\&chn=" and "\&src=" parameters)

**Owner:** Commanders Act

**Storage purpose(s):** Used for user customer journey storage for TMS deduplication (medium storage).

</details>

### CAMPAIGN

<details>

<summary>TCSESSION</summary>

**Product(s) related:** CAMPAIGN

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** Session

**Value:** CAMPAIGN Commander session ID.

**Owner:** Commanders Act

**Storage purpose(s):** Used to calculate CAMPAIGN metrics based on the session.

</details>

<details>

<summary>TCREDIRECT</summary>

**Product(s) related:** CAMPAIGN

**Type:** Cookie

**Domain:** .commander1.com​ or Customer domain

**Lifetime:** Session

**Value:** CAMPAIGN Commander redirect flag.

**Owner:** Commanders Act

**Storage purpose(s):** Used to deduplicate clicks (if redirect, just store the page view and ignore the click).

</details>

<details>

<summary>TCLANDINGURL</summary>

**Product(s) related:** CAMPAIGN

**Type:** Cookie

**Domain:** .commander1.com​

**Lifetime:** Session

**Value:** Landing page URL.

**Owner:** Commanders Act

**Storage purpose(s):** Used to store landing page URL for CAMPAIGN raw data.

</details>

### DATA

<details>

<summary>TCAUDIENCE</summary>

**Product(s) related:** Data

**Type:** Cookie

**Domain:** Customer domain

**Lifetime:** 365 days

**Value:** Audience segment storage.

**Owner:** Commanders Act

**Storage purpose(s):** Used to store the user segment for user targeting.

</details>

<details>

<summary>_TCCookieSync (Local Storage)</summary>

**Product(s) related:** DATA

**Type:** Local Storage (default)

**Domain:** /

**Lifetime:** /

**Value:** Last cookie sync date.

**Owner:** Commanders Act

**Storage purpose(s):** Used to store the date of the last cookie synchronisation with the partner (set in local storage by default, and cookie if local storage not available).

</details>

<details>

<summary>_TCCookieSync (Cookie - if Local Storage not available)</summary>

**Product(s) related:** DATA

**Type:** Local Storage (default)

**Domain:** Customer domain

**Lifetime:** 365 days

**Value:** Last cookie sync date.

**Owner:** Commanders Act

**Storage purpose(s):** Used to store the date of the last cookie synchronisation with the partner (set in local storage by default, and cookie if local storage not available).

</details>

### First Party tracking cookies

<details>

<summary>FDLB*</summary>

All possibles names:

DLBCTLYOXA \
FDLBFIRSTAPI \
FDLBFIRSTDATA \
FDLBFIRSTCAMPAIGN \
FDLBFIRSTCAMPAIGNEF \
FDLBCAMPAIGNCDOM \
FDLBFIRSTTMS \
FDLBFIRSTCMP \
FDLBFIRST \
FDLBCTLY \
FDLBFIRSTEVENTS\
\
**Product(s) related:** First domain tracking (Phoenix)

**Type:** Cookie

**Domain:** Customer domain&#x20;

**Lifetime:** Session

**Value:** Technical cookies for load balancing purposes\
**Example value:** s11|YNwyo|YNwxd

**Owner:** Commanders Act

**Storage purpose(s):** Used for internal infrastructure dispatch.\


</details>

### Phoenix

<details>

<summary>tc_caids</summary>

**Product(s) related:** Phoenix

**Type:** Cookie

**Domain:** Customer domain&#x20;

**Lifetime:** 396 days

**Value:** Technical cookie for backup Commanders Act cookies

**Owner:** Commanders Act

**Storage purpose(s):** Used for restore deleted cookies by ITP

</details>

<details>

<summary>tc_cj_ss</summary>

**Product(s) related:** Phoenix

**Type:** Cookie

**Domain:** Customer domain&#x20;

**Lifetime:** 396 days

**Value:** Technical cookie for backup Commanders Act cookie tc\_cj\_v2

**Owner:** Commanders Act

**Storage purpose(s):** Used for restore deleted cookies by ITP

</details>

<details>

<summary>tc_ss*</summary>

**Product(s) related:** Phoenix

**Type:** Cookie

**Domain:** Customer domain&#x20;

**Lifetime:** 396 days

**Value:** Technical cookie for backup custom cookies

**Owner:** Commanders Act

**Storage purpose(s):** Used for restore deleted cookies by ITP

In case your cookie "tc\_ss" contains more than 2048 characters, cookies will be created with incremented names (ex. tc\_ss1, tc\_ss2, ...)

</details>

## Custom Cookies <a href="#custom-cookies" id="custom-cookies"></a>

Users can create custom cookies with TMS Commanders Act. For example it is possible to store a URL parameter on a landing page in a cookie to make it available for further pageviews in the session. Users can choose their own name and storage duration for these cookies. Therefore it is not possible to include them in this list.
