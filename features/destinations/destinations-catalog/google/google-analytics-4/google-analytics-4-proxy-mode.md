---
description: Anonymize data before to send it to Google
---

# Google Analytics 4 - Proxy Mode

{% hint style="info" %}
The protection of user privacy has become a necessity with the implementation of the GDPR. \
In accordance with this regulation, you should delete any personally identifiable information from user data before transferring it to a tool owned by a US entity, owing to the invalidation of Privacy Shield.

The [CNIL recommended](https://www.cnil.fr/fr/cookies-et-autres-traceurs/regles/google-analytics-et-transferts-de-donnees-comment-mettre-son-outil-de-mesure-daudience-en-conformite) on June 7, 2022 that proxification should be implemented along with other specific measures to ensure the validity of the use of GA4.
{% endhint %}

The proxy mode option in the [GA4 destination](./) allows you to anonymize data before to send it to Google.

When enabled, the proxy mode gives you access to a number of options that allow you to choose granularly how each parameter should be anonymized.

<figure><img src="../../../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Some options of the proxy mode</p></figcaption></figure>

You can find below the CNIL recommandation for each parameter:&#x20;

* The absence of IP address transfer to the measurement tool servers.
* Replacement of the user identifier by the proxification server.
* Removal of the external referral site information (or "referrer") from the site.
* Removal of all parameters contained in the collected URLs (for example, UTM, as well as URL parameters allowing internal routing of the site).
* Retreatment of information that could contribute to generating a fingerprint, such as "user-agent", to remove the rarest configurations that could lead to reidentification.
* The absence of any cross-site or deterministic (CRM, unique ID) identifier collection.
* Removal of any other data that could lead to reidentification.
