# Google Tag Manager (GTM)

### Introduction

In this section, you will find a complete guide to integrate Commanders Act Consent banners in your Google Tag Manager

Enclosed you'll find two sample configuration files, a very simple setup that you'll need to reproduce you'll need to reproduce on your site. The first and most common configuration is the GTM-workspace17.json, a category-based configuration (example with only 1 category). The other possibility is a Vendor-based configuration, with only the Cact allows Statistical variable changing in GTM-workspace15.json.

{% file src="../../../../.gitbook/assets/GTM-workspace17 (1).json" %}

{% file src="../../../../.gitbook/assets/GTM-workspace15.json" %}

### Getting Started

1. &#x20;In GTM, create a new account so as not to overwrite your current configuration.
2. In this new test account, go to Admin, then on the right side of the screen click on Import Container and select the file attachment GTM-workspace17.json

<figure><img src="../../../../.gitbook/assets/gtm1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/gtm2.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/gtm3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/gtm4.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/gtm6.png" alt=""><figcaption></figcaption></figure>

3. Observe the configuration to constrain a simple Google Analytics page view tag

### Added elements

<figure><img src="../../../../.gitbook/assets/gtm7.png" alt=""><figcaption></figcaption></figure>

### Understand and personalize the json

#### Tags

1. **"Google Analytics Page view"** is only a basic tag example, both triggers are applied on
2. **"Consent Cact - Start"** tag refers to the "Consent Banner - URL" variable, and is the tag that "activates" the privacy module\* and is the only tag that will be triggered with a simple All pages trigger. **All other tags must have a trigger that includes the user's consent.** \
   \
   \*if you need more information about setup of your Consent banner, you can read our [Consent management starter kit](https://community.commandersact.com/customer-success/starter-kit/consent-management) documentation)

#### Triggers

1. **"Cact consent given Statistical"** which triggers the page view tag as soon as the user has given consent on a first visit. consent has been given by the user on a first visit. The page view hit from consent pushes a tcConsentChanged event in GTM's dataLayer for each interaction with the privacy module

| Field                     | Value                                          |
| ------------------------- | ---------------------------------------------- |
| **Trigger name**          | **Cact consent given Statistical**             |
| **Trigger Type**          | CUSTOM\_EVENT                                  |
| **Event name**            | Cact allows Statistical                        |
| **This trigger fires on** | When the user interact with the consent banner |

2. **"Cact page view consent Statistical"** which triggers the page view tag if consent has already been already been given by the user&#x20;

| Field                     | Value                                  |
| ------------------------- | -------------------------------------- |
| **Trigger name**          | **Cact page view consent Statistical** |
| **Trigger Type**          | CUSTOM\_EVENT                          |
| **Event name**            | Cact allows Statistical                |
| **This trigger fires on** | On each page view                      |

#### Tips about triggers

Cact page view consent Statistical is an arbitrary name, you can call it "Consent on page view for Analytics" or "Consent Analytics".&#x20;

Cact page view consent Statistical is dedicated to a specific category, you will need to create "Cact on page view Advertising" and/or "Consent on page view Functional" for example, depending on your needs.&#x20;

Cact consent given Statistical should also be reproduced and adapted for your other categories and coupled with page view triggers

#### Configuration example

<figure><img src="../../../../.gitbook/assets/gtm8.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
It's possible to have a double tag triggering when a page is loaded. if the tcConsentChanged event is pushed each time a page is loaded, and therefore each time a script is loaded In this case, use only Cact consent given Statistical and not Cact consent given Statistical combined with Cact page view consent Statistical .
{% endhint %}

#### Variables

1. The **"Consent banner - URL"** variable contains the URL of your consent banner. You can setup there a multi language configuration if required.\
   To obtain your privacy banner url, go on the page `Privacy banners > Deploy step`\
   You can also have a look on [this page](https://doc.commandersact.com/features/consent-management/user-guides/privacy-banners/deploy-banner) for more information
2. The **"Cact - User consent"** variable will read the TC\_PRIVACY cookie that stores the user's consent, then it will returns a string of characters with the IDs of the categories accepted by the user, separated by commas&#x20;
3. The **"Cact allows Statistical"** variable will enable you to the user's consent, it will return either allowed or refused. You will need to copy this variable and edit the ID for each category&#x20;

**Each trigger should therefore refer to the variable for its category and trigger the associated tag if it returns allowed**



{% hint style="info" %}
To make your tags are submitted to user consent, you need to verify consent in each of your triggers
{% endhint %}
