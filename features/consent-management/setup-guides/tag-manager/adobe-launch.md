---
description: Steps to implement Consent Module with Adobe Launch.
---

# Adobe Launch

Commanders Act provides a plug-in to integrate with Adobe Launch. The setup requires technical installation steps.

## Setup

Following you will find the required steps to implement a standard Commanders Act Consent setup.

1. Choose the default account configuration mode for your account ([see Settings](../../user-guides/settings.md)).
2. Setup your Commanders Act Consent categories & vendors (see [Manage Categories](../../user-guides/categories-and-tags/manage-categories.md)).
3. Create one or multiple banner templates (see [Manage Banner](../../user-guides/privacy-banners/manage-banner.md)).
4. Deploy your Consent banner templates to the Commanders Act CDN or on premise target (see [Deploy Banner](../../user-guides/privacy-banners/deploy-banner.md)).
5. Implement Commanders Act Consent JavaScript tag (see below)
6. Manage Adobe Launch tags with Commanders Act Consent (see below).

## Implement Commanders Act Consent JavaScript tag on website and inside Adobe Launch

### 1 - Website configuration

\
Delay your Adobe container. Commanders Act creates the consent variables when the privacy javascript file is loaded. You have to delay your Adobe container until Consent is ready otherwise the variables containing the consent status will be undefined.

To delay your container, update your `<script>` tags loading your Adobe container in order to execute it after Commanders Act Consent JavaScript tag is loaded.

```
<script type="text/javascript" src="/path/to/adobe_launch_script.js"></script>
```

is replaced by:

```
<script type="text/tc_privacy" src="/path/to/adobe_launch_script.js"></script>
```

The **text/javascript** script type has to be replaced by **text/tc\_privacy**. In this way, Adobe is loaded only when Commanders Act Consent is ready.

&#x20;Add the Consent javascript file (if possible, call it before Adobe container and after datalayer):

```
<script type="text/javascript">
var tCPrivacyTagManager = "adobe";
</script>
<script type="text/javascript" src="my-privacy.js"></script>
```

### 2 - Configure consent variables

When Commanders Act Consent is loaded and gets the consent, a variable tcCategoriesConsent is created by Commanders Act Consent in the Adobe datalayer:&#x20;

```
window.digitalData.user.tcCategoriesConsent = tcCategoriesConsent;
```

This variable contains the ID of the categories accepted by the user and separated by a coma.

You have to declare this variable in Adobe Launch interface, in the **Data Elements** configuration. From a Property page, open the **Data Elements** tab, then click **Add Data Element**, and add "tcCategoriesConsent" variable.

<figure><img src="../../../../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
​​If your datalayer is not set in the **digitalData** object, set the path to **tcCategoriesConsent** _(in this case the variable is created in the window scope: window.tcCategoriesConsent)_
{% endhint %}

Then, you have to create the rules that will fire your tags based on the categories ID accepted by the users. You have to create a separate rule for each category you want to use as a firing condition (ex: "Retargeting category accepted", "Analytics category accepted"...).

In the Adobe Launch interface, open the "Rules" tab and click **Create New Rule**.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-legacy-files/o/assets%2F-Lh69-tfWlhrtYE5Vhvq%2F-LlrBW2K-4nWFUr2YmRU%2F-LlrBZ6cs3CFqIq1x2WM%2Fimage.png?alt=media&#x26;token=588c7edc-17c0-40cf-85f6-84251006da2a" alt="" width="563"><figcaption></figcaption></figure>

Set a rule based on the previously created tcCategoriesConsent. \
Ex: if you want to trigger a tag based on the Retargeting category (ID 6), you will have to create a rule "if tcCategoriesConsent contains 6", then the Criteo tag has to be triggered.
