# Consent cookies exemption

For its own operations, our Consent Module sets 1st party cookies to store the [user's consent](../consent-cookie.md) and to report anonymous consent statistics.

These cookies are necessary for the proper functioning of the collection of consent and the reporting of anonymous statistics. To this regard they are exempt from the obligation of consent.

### Consent storage cookies

Consent storage cookies differ depending on the banner template used:

* **standard templates**: TC\_PRIVACY & TC\_PRIVACY\_CENTER
* **IAB TCF templates** (local storage) : TC\_PRIVACY\_IAB\_VENDORLIST & TC\_PRIVACY\_TCF&#x20;

### Cookie for anonymous statistics (TCPID)

A 1st party cookie is set to be able to collect anonymous statistics of consent: TCPID.\
We have worked together with the CNIL France to design the setting and processing of this cookie to strictly comply with the rules of the RGPD and in particular the [rules](https://www.cnil.fr/fr/cookies-et-autres-traceurs/regles/cookies-solutions-pour-les-outils-de-mesure-daudience) enacted by the CNIL in 2019.

### When are cookies exempt from consent?

In order to be exempt from consent in accordance with article 82 of the Data Protection Act, these tracers must:

* have a purpose strictly limited to measure the audience of the site or application (performance measurement, detection of navigation problems, optimization of technical performance or its ergonomics, estimation of the power of the necessary servers, analysis of content consulted) for the exclusive account of the publisher
* be used to produce anonymous statistical data only

Conversely, to be exempt from consent, **these tracers** **must not**:

* lead to a cross-checking of the data with other processing or the data to be transmitted to third parties
* do not allow the aggregate tracking of the user's navigation across different applications or websites. Any solution using the same identifier across several websites (for example via cookies placed on a third-party domain loaded by several websites) to cross, split or measure a unified coverage of a content is excluded.

#### CNIL recommendations

To put in place solutions that respect people's rights, the CNIL also recommends that:

* **users are informed** of the implementation of these tracers, for example via the privacy policy of the site or the mobile application
* **the lifespan of the tracers is limited** to a period allowing a relevant comparison of audiences over time, as is the case with a period of 13 months, and that it is not automatically extended on new visits
* the information collected through these tracers is kept for a maximum period of **25 months**
* the above-mentioned retention periods are subject to **periodic review** in order to be limited to what is strictly necessary
* for FR market : link the Consent Statistics to a category of cookies which can be turn off by the users on 'refuse all'
* for FR market : if you decide to do not link the Consent Statistics to a cookies category, you will be must to provide to your users another way to be Optout of Consent Statistics. We provide an [FR implementation guide](implementation-guide-for-exempted-consent-statistics-fr-market.md) for Optout statistics, as recommended for CNIL compliance

A subcontractor can provide a benchmark service to multiple publishers if:

* the data is collected, processed and stored independently for each publisher
* tracers are completely independent from each other\
