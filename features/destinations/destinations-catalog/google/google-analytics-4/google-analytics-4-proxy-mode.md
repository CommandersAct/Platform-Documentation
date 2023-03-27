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

<figure><img src="../../../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Some options of the proxy mode</p></figcaption></figure>

You can find below the CNIL recommandation, and for each parameter the _proxy mode_ give you a userfriendly way to manage anonymisation:&#x20;

1. _**the absence of transfer of the IP address to the servers of the analytics tool.** If a location is transmitted to the servers of the measurement tool, it must be carried out by the proxy server and the level of precision must ensure that this information does not allow the person to be re-identified (for example, by using a geographical mesh ensuring a minimum number of Internet users per cell);_\
   __\
   __**Solution:** You can choose to obfusctate the IP (the last octet (the last portion) of the IP address is replaced by 0) or to delete it completly. Obfuscation is often preferred because it allows to remove the identifying character of the IP while keeping the geolocation features of the country\

2. _**the replacement of the user identifier by the proxy server.** To ensure effective pseudonymisation, the algorithm performing the replacement should ensure a sufficient level of collision (i.e. a sufficient probability that two different identifiers will give an identical result after a hash) and include a time-varying component (adding a value to the hashed data that evolves over time so that the hash result is not always the same for the same identifier) ;_\
   __\
   __**Solution:** You can choose to pseudonymize the client id (cid) and user id (cid). This pseudonymization option consist to replace the id by a hash of id plus a salt.\
   The id will be first concatened with a salt that changes every 3h approximately and then be hased using SHA256. This allows to create anonymous ids that are identical within a session but different from session to session. This will prevent GA4 from tracking a user over time.\

3. _**the removal of external referrer information from** the site;_\
   __\
   __**Solution:** You can choose to delete it or keep only internal domains.\
   &#x20;
4. _**the removal of any parameters contained in the collected URLs** (e.g. UTMs, but also URL parameters allowing internal routing of the site);_\
   __\
   __**Solution:** You can choose to delete all url parameters, keep only specific parameters and/or keep UTMs in some case\

5. _**reprocessing of information that can be used to generate a fingerprint**, such as user-agents, to remove the rarest configurations that can lead to re-identification;_\
   __\
   __**Solution:** Choosing to delete completly the user-agent seems to be the best option.\

6. _**the absence of collection of cross-site or lasting identifiers** (CRM ID, unique ID);_\
   __\
   __**Solution:**  Use the [Properties Transformation](../../../advanced-mapping.md#transform-data-before-it-gets-to-the-destination.) feature or the [Data Cleansing](../../../../data-quality/data-cleansing/) feature to treat on a case by case basis by deleting/hashing/transforming your properties (see [Manage custom PII data](google-analytics-4-proxy-mode.md#2.-manage-custom-pii-data) below)\
   __
7. _**the deletion of any other data that could lead to re-identification**._\
   __\
   __**Solution:** Use the [Properties Transformation](../../../advanced-mapping.md#transform-data-before-it-gets-to-the-destination.) feature or the [Data Cleansing](../../../../data-quality/data-cleansing/) feature to treat on a case by case basis by deleting/hashing/transforming your properties (see [Manage custom PII data](google-analytics-4-proxy-mode.md#2.-manage-custom-pii-data) below)

## 2. Manage custom PII data

In addition to the GA4 proxy mode, you can also use on each destination, the [Properties Transformation](../../../advanced-mapping.md#transform-data-before-it-gets-to-the-destination.) feature or the [Data Cleansing](../../../../data-quality/data-cleansing/) feature to transform/delete/hash any event property before to send it to the partner.

### 2.1. Properties transformation on a specific destination

<figure><img src="../../../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Properties transformation section on each destination settings step</p></figcaption></figure>

### 2.2. Data Cleansing for all destinations

<figure><img src="../../../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Data Cleansing feature</p></figcaption></figure>
