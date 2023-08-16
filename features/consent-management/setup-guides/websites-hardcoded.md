---
description: Steps to hard code Commanders Act Consent on websites.
---

# Websites (Hardcoded)

Commanders Act Consent can be directly integrated with websites. The setup requires technical installation steps.

## Setup

Following you will find the required steps to implement a standard Commanders Act Consent setup.

1. Choose the default account configuration mode for your account (see [Settings](../user-guides/settings.md)).
2. Setup your Commanders Act Consent categories & vendors (see [Manage Categories](../user-guides/categories-and-tags/manage-categories.md)).
3. Create one or multiple banner templates (see [Manage Banner](../user-guides/privacy-banners/manage-banner.md))
4. Deploy your Commanders Act Consent banner templates to the Commanders Act CDN or on premise target (see [Deploy Banner](../user-guides/privacy-banners/deploy-banner.md)).
5. Install Commanders Act Consent JavaScript tag (see below)
6. Manage onsite tags with Commanders Act Consent (see below<mark style="color:red;">)</mark>.

## Install Commanders Act Consent script

To hard code Commanders act Consent on websites you need to add following JavaScript code to your website. This snippet should be added to the `<head>` of your website.

```
<script type="text/javascript" src="{{ privacy_tag_url }}"></script>
```

`{{ privacy_tag_url }}` has to be replaced with your privacy JavaScript tag URL. This URL can be found in the `GENERATE & DEPLOY` tab of each privacy banner.

<figure><img src="../../../.gitbook/assets/image (222).png" alt=""><figcaption></figcaption></figure>

## Manage onsite tags with Commanders Act Consent

### **Add tag triggers with OnSite API**

We recommend to use our [OnSite API](../onsite-api/)<mark style="color:red;">,</mark> to trigger your tags only if user has accepted the related category.\
If you are looking for your categories  ID's, please refer to the section '[Manage Categories](../user-guides/categories-and-tags/manage-categories.md)'

### Add tag triggers without OnSite API

If, for some specific reasons, you cannot use our OnSite API, there's an alternative approach.

Commanders Act can manage onsite JavaScript tags by wrapping them in a script tag with a custom MIME type.

{% hint style="info" %}
This approach only works when you install Commanders Act Consent tag in the `<head>` of the document (e.g. not when injecting the Commanders Act Consent tag via Google Tag Manager)!
{% endhint %}

This Commander Act wrapper does only fire that wrapped JavaScript code in case a visitor provided consent for the specified privacy category ID.

```
<script type="text/tc_privacy" data-category="{{ category_or_sub-category_id }}" data-vendor="{{ vendor_id }}">
    {{ tag_javascript_code }}
</script>
```

The `<script>` has to have `type="text/tc_privacy"` .

`{{ tag_javascript_code }}` has to be replaced with the JavaScript code of the tag you want to manage with Commanders Act Consent.

`{{ category_or_subcategory_id }}` has to be replaced with the category or sub-category of the Commanders Act Consent category that should manage this tag (see [Manage Categories](../user-guides/categories-and-tags/manage-categories.md)). Be careful when you create sub-categories associated to a category: you have to enter the sub-category ID in the attribute, not the category ID, as the user will be able to activate or deactivate only sub-categories and not the main category in the banner:

<figure><img src="../../../.gitbook/assets/image (190).png" alt="" width="413"><figcaption></figcaption></figure>

`{{ vendor_id }}` has to be replaced with the vendor ID of the vendor related to the tag (Only available when native vendors are activated for the account).

### Example

Following examples shows how you would manage a Criteo Tag based on a Consent category named "retargetting".&#x20;

<figure><img src="../../../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>

"Retargetting" was assigned to sub-category ID 6. In case a sub-category is used you should never use the main category (2 in this case) to manage tags.

The Tag wrapper for the Criteo JavaScript tag might look like this (example shortened):

```javascript
<script type="text/tc_privacy" data-category="6" src="//static.criteo.net/js/ld/ld.js" async="true">
</script>

<script type="text/tc_privacy" data-category="6">
    window.criteo_q = window.criteo_q || [];
    window.criteo_q.push(...);
</script>
```
