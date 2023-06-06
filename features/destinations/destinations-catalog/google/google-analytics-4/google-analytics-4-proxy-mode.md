---
description: Anonymize data before to send it to Google
---

# Google Analytics 4 - Proxy Mode

{% hint style="info" %}
The protection of user privacy has become a necessity with the implementation of the GDPR. \
In accordance with this regulation, you should delete any personally identifiable information from user data before transferring it to a tool owned by a US entity, owing to the invalidation of Privacy Shield.

The [CNIL recommended](https://www.cnil.fr/fr/cookies-et-autres-traceurs/regles/google-analytics-et-transferts-de-donnees-comment-mettre-son-outil-de-mesure-daudience-en-conformite) on June 7, 2022 that proxification should be implemented along with other specific measures to ensure the validity of the use of GA4.
{% endhint %}

## 1. Use proxy options in the destination settings

The proxy mode option in the [GA4 destination](./) allows you to anonymize data before to send it to Google.

When enabled, the _proxy mode_ gives you access to a number of options that allow you to choose granularly how each parameter should be anonymized.

<figure><img src="../../../../../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>Some options of the proxy mode</p></figcaption></figure>

You can find below the CNIL recommandation, and for each parameter the _proxy mode_ give you a userfriendly way to manage anonymisation:&#x20;

1. _**the absence of transfer of the IP address to the servers of the analytics tool.** If a location is transmitted to the servers of the measurement tool, it must be carried out by the proxy server and the level of precision must ensure that this information does not allow the person to be re-identified (for example, by using a geographical mesh ensuring a minimum number of Internet users per cell);_\
   \
   **Solution:** You can choose to obfusctate the IP (the last octet (the last portion) of the IP address is replaced by 0) or to delete it completly. Obfuscation is often preferred because it allows to remove the identifying character of the IP while keeping the geolocation features of the country\

2. _**the replacement of the user identifier by the proxy server.** To ensure effective pseudonymisation, the algorithm performing the replacement should ensure a sufficient level of collision (i.e. a sufficient probability that two different identifiers will give an identical result after a hash) and include a time-varying component (adding a value to the hashed data that evolves over time so that the hash result is not always the same for the same identifier) ;_\
   \
   **Solution:** You can choose to pseudonymize the client id (cid) and user id (uid). This pseudonymization option consist to replace the id by a hash of id plus a salt.\
   The id will be first concatened with a salt that changes every 3h approximately and then be hased using SHA256. This allows to create anonymous ids that are identical within a session but different from session to session. This will prevent GA4 from tracking a user over time.\

3. _**the removal of external referrer information from** the site;_\
   \
   **Solution:** You can choose to delete it or keep only internal domains.\
   &#x20;
4. _**the removal of any parameters contained in the collected URLs** (e.g. UTMs, but also URL parameters allowing internal routing of the site);_\
   \
   **Solution:** You can choose to delete all url parameters, keep only specific parameters and/or keep UTMs in some case\

5. _**reprocessing of information that can be used to generate a fingerprint**, such as user-agents, to remove the rarest configurations that can lead to re-identification;_\
   \
   **Solution:** Choosing to delete completly the user-agent seems to be the best option.\

6. _**the absence of collection of cross-site or lasting identifiers** (CRM ID, unique ID);_\
   \
   **Solution:**  Use the [Properties Transformation](../../../advanced-mapping.md#transform-data-before-it-gets-to-the-destination.) feature or the [Data Cleansing](../../../../data-quality/data-cleansing/) feature to treat on a case by case basis by deleting/hashing/transforming your properties (see [Manage custom PII data](google-analytics-4-proxy-mode.md#2.-manage-custom-pii-data) below)\

7. _**the deletion of any other data that could lead to re-identification**._\
   \
   **Solution:** Use the [Properties Transformation](../../../advanced-mapping.md#transform-data-before-it-gets-to-the-destination.) feature or the [Data Cleansing](../../../../data-quality/data-cleansing/) feature to treat on a case by case basis by deleting/hashing/transforming your properties (see [Manage custom PII data](google-analytics-4-proxy-mode.md#2.-manage-custom-pii-data) below)

## 2. Manage custom PII data

In addition to the GA4 proxy mode, you can also use on each destination, the [Properties Transformation](../../../advanced-mapping.md#transform-data-before-it-gets-to-the-destination.) feature or the [Data Cleansing](../../../../data-quality/data-cleansing/) feature to transform/delete/hash any event property before to send it to the partner.

### 2.1. Properties transformation on a specific destination

<figure><img src="../../../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Properties transformation section on each destination settings step</p></figcaption></figure>

### 2.2. Data Cleansing for all destinations

<figure><img src="../../../../../.gitbook/assets/image (6) (2).png" alt=""><figcaption><p>Data Cleansing feature</p></figcaption></figure>

## 3. Impact analysis and open suggestions

| CNIL recommandation                                                               | Analysis                                                                                                                                                   | Suggestion/Impact                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Absence of IP address transfer to measurement tool servers                        | This point is normal and standard.                                                                                                                         | <p>Anonymize IPs by removing the last 3 characters. <br>Impact: This may result in a loss of location precision, going from a measurement at the city level to that of the region.</p>                                                                                                                                                                                                                                                                                          |
| Replacement of user identifier by the proxy server                                | The CNIL doubts that Google does not use this data in conjunction with other third-party data.                                                             | <p>Add pseudonymisation before sending the ID.<br>No impact.</p>                                                                                                                                                                                                                                                                                                                                                                                                                |
| Removal of external referrer information (or "referrer") from the site            | Complete removal of the referrer is a surprising proposition, while just reducing it to the domain name is common in other tools (Safari, Adblockers, ...) | <p>Reduce the referrer to the domain name, which is a simple statistical measure of audience.<br>If this suggestion is followed, there will be no impact. (If the CNIL recommendation is followed, the tool will become useless or almost useless)<br>You can also choose to only authorize internal domains, in this case the impact can be important, especially on source traffic reports.</p>                                                                               |
| Removal of any parameters contained in collected URLs                             | It is legitimate to remove URL parameters containing personal information, but maybe not general information like utm\_campaigns.                          | Remove URL parameters on a case-by-case basis if they contain personally identifiable data. Utm\_campaigns can be kept if they are properly managed, but the question arises for advertising click IDs such as fbclid and gclid. If the CNIL recommendation is followed, the tool will become useless or almost useless, while if our recommendation is followed, there will be little impact. In case of gclid removal, utms will need to be used to tag Google Ads campaigns. |
| Retreatment of information that could contribute to generating a fingerprint      | This request is legitimate and common and will be implemented in browsers in the future.                                                                   | <p>Remove unnecessary information from the user agent to minimize loss of granular information such as the phone model.<br>Choosing to delete completly the user-agent seems to be the easiest option.<br>Impact: very low</p>                                                                                                                                                                                                                                                  |
| Absence of any cross-site or deterministic (CRM, unique ID) identifier collection | <p>This request is considered irrelevant as long as consent is obtained.<br>These IDs cannot be used by Google for other data cross-referencing.</p>       | <p>It is recommended to request consent for the use of these IDs and to treat them securely if consent is given.<br>But you may want to hash all this ids before to send it to Google (in that case you can use Properties transformation)</p>                                                                                                                                                                                                                                  |

## Quick setup

1.  **Update your client-side gtag**\
    As with classical GA4 server-side setups, you need to setup a single initial client-side Gtag tag which will only be triggered once per visit and will send an empty initialization event. \
    This is necessary due to current [limitations of Google's protocol](https://developers.google.com/analytics/devguides/collection/protocol/ga4#caveats\_to\_measurement\_protocol).\


    Then the particularity with the _proxy mode_ is that you have to alter the GA4 hit URL, replacing _google-analytics.com_ with the Commanders Act server-side collection URL. This is done via the native GA parameter: `transport_url` (Example code provided below).\
    ![](<../../../../../.gitbook/assets/MicrosoftTeams-image (2).png>)\


    Consequently, this first hit is no longer sent to Google, but to Commanders Act server, which transforms it into a CA event. This event will then be sent to your GA4 destination where it will be processed (pseudonymized, etc. depending on the chosen settings) before being sent back to Google.\


    Apart from this first client-side hit, all other events from the website should be sent from any source, for instance through our function cact('trigger', 'myEventName', ...). These events will also, of course, reach your GA4 destination where the data will be pseudonymized according to the settings of the destination.
2. **Setup your GA4 destination**\
   \- In the settings tab, check the "Enable proxy mode" option and choose wich pseudonymisation/treatment you want to apply.\
   \- If needed hash your custom PII data through the smart mapping, properties transformation or [Data Cleansing](../../../../data-quality/data-cleansing/)
3. (**Optional) Check that all the sent PII data are properly pseudonymised**\
   Go through [Event Inspector](../../../live-event-inspector.md) and inspect outgoing events.

