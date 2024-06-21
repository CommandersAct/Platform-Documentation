---
description: Steps to implement Commanders Act Consent Module with Google Tag Manager.
---

# Google Tag Manager (GTM) - Consent Mode

Commanders Act provides a tag template to manage the "[Consent Mode](https://developers.google.com/tag-platform/devguides/consent)" in Google Tag Manager.\
This seamless integration takes advantage of our Commanders Act OnSite API.&#x20;

## Setup

Summarizing all recommended steps:

1. Access [GTM](https://tagmanager.google.com/).
2. Select your "Web" type container.
3. Add our tag template from the "[Community Template Gallery](https://tagmanager.google.com/gallery/#/owners/TagCommander/templates/GTM-OnSite-API)".
4. Configure the related tag and its trigger.
5. Configure your third-party vendor tags.
6. Test and deploy your container.

## Configure the related tag and its trigger

Following the above steps, adding our template "[**Commanders Act CMP**](https://tagmanager.google.com/gallery/#/owners/TagCommander/templates/GTM-OnSite-API)" from the Google "Community Template Gallery", you're presented with the following "**Tag Configuration**" which is the core area where you can manage your consent needs with GTM:

<figure><img src="../../../../.gitbook/assets/onsite_api1.png" alt=""><figcaption><p>The "Commanders Act CMP" configuration in GTM.</p></figcaption></figure>

First, you need to input your consent category identifiers for the following **7 categories**: `Ad Storage`, `Analytics Storage`, `Functionality Storage`, `Personalization Storage`, `Security Storage`, `Ad User Data` and `Ad Personalization`. You can define/find these identifiers by logging in to our platform and follow the section:\
`(A)`"**Data Governance**" → `(1)`"**Consent Management**" → `(2)`"**Categories**".

<figure><img src="../../../../.gitbook/assets/onsite_api2.png" alt=""><figcaption><p>Define/find your category identifiers.</p></figcaption></figure>

Your identifiers are shown between round parentheses (see highlighted in green below):\


<figure><img src="../../../../.gitbook/assets/image (515).png" alt="" width="518"><figcaption></figcaption></figure>

{% hint style="info" %}
If you have sub-categories with the same scope of the five defined by Google, you need to use their ids instead of the main category ones. You can also rename your categories or change their ids by checking the subsection "[**Managing categories**](https://community.commandersact.com/trustcommander/user-guides/categories-and-tags/manage-categories#managing-categories)".
{% endhint %}

If your CMP loads asynchronously, it might not always run before your GTM container. That’s why you have the option to set a "**Wait for update**" value in milliseconds to control how long to wait before data is sent. This field is optional and its default value is 0. In case you need to set it, we recommend starting from the base value of 500 milliseconds.

You also need to set the default status, for each of the 7 categories, before users interact with your [**privacy banner**](https://community.commandersact.com/trustcommander/user-guides/privacy-banners) and taking into account region-specific behavior. This is done by clicking the "Add Row" button and selecting either "Denied" or "Granted" to match with your input regions and/or sub-regions.&#x20;

{% hint style="info" %}
Ensure that your default command accounts for regional variations in your consent strategy. For more information on customizing the default command, you can see Google’s documentation [here](https://developers.google.com/tag-platform/devguides/consent#region-specific\_behavior).
{% endhint %}

<figure><img src="../../../../.gitbook/assets/onsite_api4.png" alt=""><figcaption><p>Select your default status for each category and by region and sub-region.</p></figcaption></figure>

To make sure that the consent is correctly managed by GTM with third-party vendor tags, we strongly recommend to enable reactive events. Turn on the `(3)` "**Advanced Features**", `(4)` "**Activate Reactive Events**" and `(5)` "**Activate \[Storage-Name] Reactive Event**" for each \[Storage Name] you're using. Finally, enter their `(6)` "**Event Name**". These events will be used in the next section when configuring your third-party vendor tags.

<figure><img src="../../../../.gitbook/assets/onsite_api5.png" alt=""><figcaption><p>Reactive events activation under "Advanced Features".</p></figcaption></figure>

You also have the option to directly inject your CMP script by turning on the `(7)` "**Advanced Features**", `(8)` "**Inject CMP Script**" and input your `(9)` "**URL**".

<figure><img src="../../../../.gitbook/assets/onsite_api6.png" alt=""><figcaption><p>Inject your script directly using this template.</p></figcaption></figure>

Disabling the default consent may come handy when you don't want to use the Consent Mode.\
This is done by turning on the `(10)` "**Advanced Features**" and `(11)` "**Disable Default Consent**".

<figure><img src="../../../../.gitbook/assets/onsite_api7.png" alt=""><figcaption><p>Disable the "Default Consent".</p></figcaption></figure>

As the last step, you need to select the "Consent Initialization - All Pages" trigger in the "**Triggering**" lower area:

<figure><img src="../../../../.gitbook/assets/image (202).png" alt=""><figcaption><p>Select "Consent Initialization - All Pages" as trigger.</p></figcaption></figure>

### Modify Permissions

If your banner is hosted on your servers (on premise) or if you use our CDN 1st feature, then you need to update the Permissions of our template.

Simply add your host URL in the tab "Injects scripts" (see block "allowed patterns").

<figure><img src="../../../../.gitbook/assets/image (518).png" alt=""><figcaption></figcaption></figure>

## Configure your third-party vendor tags

While Google native product tags, such as "Google Analytics" or "Google Ads" ones, work out of the box, third-party vendor tags require additional settings to properly operate with the user consent. First, open your tag configuration and check under the `(12)` "**Advanced Settings**" and `(13)`"**Consent Settings**" if a consent type (E.g. "_ad\_storage_") is already preconfigured, if not you need to add it by selecting the option `(14)` "**Require additional consent for tag to fire**" and `(15)` input the consent type(s) you want to include.

<figure><img src="../../../../.gitbook/assets/image (215).png" alt=""><figcaption></figcaption></figure>

Then, you need to configure its triggers and this is where we're going to use our reactive events we prepared in the previous section. Locate the "**Triggering**" area in your tag configuration and add a "[**Trigger Group**](https://support.google.com/tagmanager/answer/9164222?hl=en)".

<figure><img src="../../../../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

In the trigger group add `(16)` any preexisting triggers and `(17)`a trigger named as your configured reactive event.

<figure><img src="../../../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

The latter has to be configured as a `(18)`"**Custom Event**" with the same `(19)`"**Event Name**" you used in the previous section and it has to fire on `(20)`"**All Custom Events**".

<figure><img src="../../../../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

This completes your configuration. You can now start the testing phase, leading to the final deployment in production. Learn more on how you can configure and run tests with your tags in GTM by checking the section "[**Consent configuration**](https://support.google.com/tagmanager/answer/10718549/?hl=en-GB)" in the "[**Help Center**](https://support.google.com/tagmanager/)".
