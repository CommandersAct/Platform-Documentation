---
description: >-
  This page is to the attention the customers using the Commanders Act SDK with
  the IAB Consent Module in their mobile application
---

# IAB TCF v2.2 Migration guide App

## Introduction

Here's the 2 steps to follow to remains compliant with the TCF on your mobile application&#x20;

{% hint style="warning" %}
Requirements\
To be allowed to migrate on IAB TCF v2.2, your application must use the v5 of our SDKs\
If you're still using the v4, please refer to the main [SDK Migration Guide](https://doc.commandersact.com/getting-started/integrating-your-data/migration-guides-to-the-platform-x/migrate-from-old-mobile-sdk)
{% endhint %}

{% hint style="info" %}
Please note: this documentation is a user friendly step by step guide. For technical details please refer to our GitHub [Android](https://github.com/CommandersAct/AndroidV5/tree/master/TCIAB) and [iOS](https://github.com/CommandersAct/iOSV5/tree/master/TCIAB)
{% endhint %}

### 1-Update the SDK Module

Simply download the latest versions of our TCIAB SDK Modules

* [Android](https://github.com/CommandersAct/AndroidV5/tree/master/TCIAB)
* [iOS](https://github.com/CommandersAct/iOSV5/tree/master/TCIAB)

### 2-Update the json files

**Upload the latest version to update your offline json's**

* [vendor-list.json](https://cdn.trustcommander.net/iab-v2/gvl-v3/vendor-list.json)
* [purposes-xx.json](https://cdn.trustcommander.net/iab-v2/gvl-v3/purposes-fr.json) (required if you're using other languages then EN, this link example is for FR language)
* your privacy json file updated (needs to be modified, following the step "Update the content of your privacy json file")

**Upload your CDN json file**

Your privacy json file updated needs to be uploaded on CDN Commanders Act, please contact your consultant or our support team to upload the latest version of your json on our servers. (the content of this json file needs to be updated, following the next step.)\


**Update the content of your privacy json file**

1. Verify your vendor list    `"vendors": "15,48,501,506,520,539,512,895",`\
   \*if you left the "vendors" empty, it will be considered as ALL vendors by our SDK\
   Pay attention to your Vendor List, some Vendors aren't existing anymore in the GVL v3\

2.  Add the new required fields\
    `texts -> generic -> "illustationsButton": "illustrations"` &#x20;

    `texts -> generic -> "dataCategoriesDef" : "Data Categories"` &#x20;

Full json example:&#x20;

```
{
	"information": {
		"update": "2023-06-30",
		"version": "1",
		"vendors": "8,241",
		"google_vendors" : "323,389,385,424",
		"consentDurationInMonths": 6,
		"significantChanges": "",
		"resetSave": ""
	},
	"components": {
		"firstLayerButton": ["RefuseAll", "Detail", "AcceptAll"],
		"secondLayerButton": ["RefuseAll", "Save", "AcceptAll"]
	},
	"customisation": {
		"content": {
			"fontcolor": "#000000",
			"backgroundcolor": "#ffffff",
			"bordercolor": "#806423"
		},
		"button": {
			"fontcolor": "#ffffff",
			"backgroundcolor": "#4287f5",
			"disabledBackground": "#E1E1E1",
			"linkcolor": "#0907F7"
		},
		"order": ["Custom", "IAB"]
	},
	"texts": {
		"generic": {
			"saveButton": "Save & Exit",
			"detailButton": "Details",
			"acceptAllButton": "Accept All",
			"refuseAllButton": "Refuse All",
			"vendorButton": "Vendors",
			"purposeButton": "Purposes",
			"legalButton": "Legals",
			"illustationsButton": "illustrations",
			"backButton": "Back",
			"purposeDef": "Purposes",
			"consentDef": "Consent",
			"legIntPurposeDef": "Legitimate Interest",
			"flexiblePurposeDef": "Flexible Purpose",
			"specialPurposeDef": "Special Purpose",
			"featureDef": "Features",
			"specialFeatureDef": "Special Features",
            		"dataCategoriesDef" : "Data Categories",
			"partnersLinkText": "our partners",
			"relatedVendorsButton": "show related vendors",
			"month": "month",
			"day": "day",
			"seconds": "seconds",
			"hours": "hours"
		},
		"popup": {
			"title": "We respect your privacy",
			"content": "We and our partners use technologies, such as cookies, and process personal data, such as IP addresses and cookie identifiers, to personalise ads and content based on your interests, measure the performance of ads and content, and derive insights about the audiences who saw ads and content. Click below to consent to the use of this technology and the processing of your personal data for these purposes. You can change your mind and change your consent choices at any time by returning to this site.\n",
			"purposeTitle": "We and our {total_number} partners:",
			"specialPurposeTitle": "We need your consent for all the purposes above, but we have legitimate interest for these purposes:",
			"featureTitle": "For some of the purposes above we and our partners:",
			"specialFeatureTitle": "For some of the purposes above we and our partners:"
		},
		"purposes": {
			"title": "Find out more about how your personal data is processed and set your preferences below.",
			"content": "You can set your consent preferences and determine how you want your data to be used based on the purposes below. You may set your preferences for us independently from those of third-party partners. Each purpose has a description so that you know how we and partners use your data.",
            "privacy_policy_text": "Check our privacy policies",
			"privacy_policy_url": "https://ourcompany.com/privacypolicies"
		},
		"vendors": {
			"title": "See the partners we work with below. Expend each one to see how they process your data.",
			"content": "You can set consent preferences for individual third-party partners we work with below. Expand each company list item to see what purposes they use data for to help make your choices. In some cases, companies may use your data without asking for your consent, based on their legitimate interests. You can click on their privacy policy links for more information and to object to such processing.",
			"privacyPolicyText": "Privacy Policy",
			"deviceStorageTitle": "Storage Type:",
			"deviceStorageCookieLifetime": "Cookie lifetime: ",
			"deviceStorageOther": "Others",
			"deviceStorageCookies": "Cookies",
            "googleVendorsDef" : "Google Ad Technology Providers",
            "domainsDef" : "Domain list", 
            "IABVendorsDef" : "IAB TCF Vendors"
		},
		"others": {
			"title_purpose": "Other categories EN",
			"title_vendors": "Other vendors EN"
		}
	},
	"texts_fr": {
		"generic": {
			"saveButton": "J'accepte",
			"detailButton": "Détail",
			"acceptAllButton": "Tout Accepter",
			"refuseAllButton": "Tout Refuser",
			"vendorButton": "Afficher les partenaires",
			"purposeButton": "Afficher les finalités",
			"legalButton": "Informations légales",
            "illustationsButton": "illustrations",
			"backButton": "Retour",
			"purposeDef": "Finalités",
			"consentDef": "Consentement",
			"legIntPurposeDef": "Intérêts légitimes",
			"flexiblePurposeDef": "Finalités flexibles",
			"specialPurposeDef": "Finalités spéciales",
			"featureDef": "Fonctionnalités",
			"specialFeatureDef": "Fonctionnalités spéciales",
            "dataCategoriesDef" : "Categories de Data",
			"partnersLinkText": "nos partenaires",
			"relatedVendorsButton": "Voir les partenaires",
			"month": "mois",
			"day": "jours",
			"seconds": "secondes",
			"hours": "heures"
		},
		"popup": {
			"title": "Le respect de votre vie privée est notre priorité",
			"content": "Nous et nos {total_number} partenaires pouvons stocker et/ou accéder à des informations sur un terminal, sélectionner des publicités standard, créer un profil personnalisé de publicités, sélectionner des publicités personnalisées, mesurer la performance des publicités, mesurer la performance du contenu, exploiter des études de marché afin de générer des données d’audience, développer et améliorer les produits, créer un profil pour afficher un contenu personnalisé, sélectionner du contenu personnalisé, mesurer la performance des publicités, exploiter des études de marché afin de générer des données d’audience, développer et améliorer les produits, sélectionner des publicités standard, mesurer la performance du contenu, créer un profil personnalisé de publicités, sélectionner des publicités personnalisées, créer un profil pour afficher un contenu personnalisé, sélectionner du contenu personnalisé. Ces technologies peuvent traiter des données personnelles comme l'adresse IP et les données de navigation pour assurer la sécurité, prévenir la fraude et déboguer, diffuser techniquement les publicités ou le contenu. Elles peuvent mettre en correspondance et combiner des sources de données hors ligne, recevoir et utiliser des caractéristiques d’identification d’appareil envoyées automatiquement, relier différents terminaux. Elles peuvent analyser activement les caractéristiques du terminal pour l’identification, utiliser des données de géolocalisation précises.\n",
			"purposeTitle": "Gérer vos préférences",
			"specialPurposeTitle": "Gérer vos special purposes",
			"featureTitle": "Gérer vos features ",
			"specialFeatureTitle": "Gérer vos specialFeatures"
		},
		"purposes": {
			"title": "Gérer vos préférences P",
			"content": "Nos partenaires P et nous déposons des cookies afin d'assurer la sécurité, améliorer votre expérience digitale et afficher des publicités et contenus personnalisés Vous pouvez accepter ou refuser ces différentes opérations.",
			"privacy_policy_text": "Notre politique de confidentialitée",
			"privacy_policy_url": "https://ourcompany.com/privacypolicies"
		},
		"vendors": {
			"title": "Gérer vos préférences V",
			"content": "Nos partenaires V et nous déposons des cookies afin d'assurer la sécurité, améliorer votre expérience digitale et afficher des publicités et contenus personnalisés Vous pouvez accepter ou refuser ces différentes opérations.",
			"privacyPolicyText": "Politique de confidentialité",
			"deviceStorageTitle": "Type de stockage:",
			"deviceStorageCookieLifetime": "Durée du cookie: ",
			"deviceStorageOther": "Autres",
			"deviceStorageCookies": "Cookies",
            "googleVendorsDef" : "Partenaires Google Ad Technology",
            "domainsDef" : "liste des domaines utilisés", 
            "IABVendorsDef" : "liste des partenaires IAB"
		},
		"others": {
			"title_purpose": "Other categories FR",
			"title_vendors": "Other vendors FR"
		}
	},
	"categories": [{
			"name": "Statistics",
			"ID": "1",
			/* Ajouter "isMandatory": "true" pour bloquer la category sur ON 
			   If you are using sub-categories, only sub can be marked as mandatories */
			"isMandatory": "true",
			"related_vendors": [1],
			"description": "These cookies allow us analyze user behavior on the site, measure and improve performance and the quality of our service."
		},
		{
			"name": "Advertising",
			"ID": "2",
			"related_vendors": [2],
			"description": "These cookies allow us display adverts matching your interests on the websites you visit."
		},
		{
			"name": "Big category",
			"ID": "30",
			"description": "Here you can select the vendors.",
			"subcategories": [{
					"name": "GA",
					"ID": "31",
					"description": "Should we send information to GA."
				},
				{
					"name": "Xiti",
					"ID": "32",
					"description": "Should we send information to AT Internet."
				},
				{
					"name": "Vendor3",
					"ID": "33",
					"related_vendors": [1, 2],
					"description": "Should we send information to this vendor3."
				}
			]
		}
	],
	"vendors": [{ /* list here all the not IAB Vendors */
			"name": "Commanders Act",
			"ID": "1",
			"description": "Allow Commanders Act",
			"privacy_policy": "http://commandersact.com/privacypolicy"
		},
		{
			"name": "Another non IAB Vendor",
			"ID": "2",
			"description": "The desc of another vendor",
			"privacy_policy": "http://anothervendor.free.fr/privacypolicy"
		}
	],
	"categories_fr": [{
			"name": "Statistiques",
			"ID": "1",
			"related_vendors": [1],
			"description": "Avec cette catégorie on remonte les stats."
		},
		{
			"name": "Pub",
			"ID": "2",
			"related_vendors": [2],
			"description": "Pour afficher de superbes pubs personalisées"
		},
		{
			"name": "Super cat",
			"ID": "30",
			"description": "Une super cat.",
			"subcategories": [{
					"name": "Sous cat 1",
					"ID": "31",
					"description": "Mais on peut choisir que cette sous cat."
				},
				{
					"name": "Sous cat 2",
					"ID": "32",
					"description": "Ou alors uniquement celle-ci."
				},
				{
					"name": "Sous cat 3",
					"ID": "33",
					"related_vendors": [1, 2],
					"description": "Ou plus en fait, mais la 3 c'est pareil."
				}
			]
		}
	],
	"vendors_fr": [{
			"name": "Commanders Act",
			"ID": "1",
			"description": "Permettre à Commanders Act d'envoyer des informations",
			"privacy_policy": "http://commandersact.com/privacypolicy"
		},
		{
			"name": "Autre Vendors",
			"ID": "2",
			"description": "Permettre à cet autre vendor d'envoyer pleins d'informations",
			"privacy_policy": "http://anothervendor.free.fr/privacypolicy"
		}
	]
}
```



{% hint style="info" %}
The value {total\_number} in the "purposeTitle" is a dynamic field. The total number of your IAB vendors will be displayed here
{% endhint %}

{% hint style="danger" %}
The deadline to migrate is November 20, 2023
{% endhint %}
