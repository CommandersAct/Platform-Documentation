---
description: Steps to implement Consent Module with TMS Commanders Act
---

# Commanders Act TMS

Consent Module and TMS Commanders Act are natively integrated with each other. This setup requires minimal technical knowledge and can be done entirely in the interface.

## Setup

Following you will find the required steps to implement a standard Commanders Act Consent module setup.

1. Choose the default account configuration mode for your account (see [Options](../../user-guides/settings.md)).
2. Setup your Consent categories & vendors (see [Manage Categories](../../user-guides/categories-and-tags/manage-categories.md)).
3. Assign your Consent categories & vendors to your Commanders Act Web Container tags (see [Assign categories](../../user-guides/categories-and-tags/assign-categories.md))
4. Create one or multiple Consent banner templates (see [Manage Banner](../../user-guides/privacy-banners/manage-banner.md))
5. Deploy your Consent banner templates to the Commanders Act CDN or on premise target (see [Deploy Banner](../../user-guides/privacy-banners/deploy-banner.md)).
6. Connect your privacy banner templates with Commanders Act  Web Container and implement rules for which the banner should be played out (see below).

## Install Consent banner with TMS Commanders Act&#x20;

To deploy a Consent banner with the Commanders Act TMS it needs to be linked to a container.  Commanders Act TMS  can then be use to implement detailed rules for which a Consent banner is shown to visitors.

Implement rules to display Consent banners

`Sources > Overview > Web Containers > tab RULES > Privacy Banners Constraints​`

<figure><img src="../../../../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure>

In  Commanders Act TMS  it is possible to provide exact conditions to decide when each of the linked privacy banners should be shown to visitors. Typical use cases consist of:

* Implement different banner for different languages or regions
* Avoid to deploy the banner on legal pages (privacy policy) so that users can read them before providing consent.
* Implement AB test for two banner designs.

You can create constrains under the `PRIVACY BANNERS` section to define under which conditions a privacy banner should be shown. Privacy banner constraint work the same way as tag constraints. Please reference constraints in the Web Container documentation for more information.

<figure><img src="../../../../.gitbook/assets/image (169).png" alt=""><figcaption><p>Example: The selected banner would only load in case the data layer property env_language has the value FR.</p></figcaption></figure>

{% hint style="info" %}
You have to first deploy a banner to the Commanders Act CDN or on premise location before being able to configure constraints (see [Deploy Banner](../../user-guides/privacy-banners/deploy-banner.md)).
{% endhint %}

## Link Consent banner with Commanders Act Web Container <a href="#link-trustcommander-banner-with-tagcommander-container" id="link-trustcommander-banner-with-tagcommander-container"></a>

`Sources > Overview > Web Containers > tab GENERATE`

<figure><img src="../../../../.gitbook/assets/image (195).png" alt=""><figcaption><p>Example: Add privacy banner to Commanders Act TMS container.</p></figcaption></figure>

Commanders Act TMS makes it easy to implement Consent banner on websites. To link a privacy banner with a Commanders Act TMS container it just has to be activated in the `GENERATE` tab with the `ACTIVATION` checkbox. This installs the selected privacy banner in the generated container version.

<figure><img src="../../../../.gitbook/assets/image (203).png" alt=""><figcaption><p>Example: Consent banners are now deployed with the Commanders Act TMS container.</p></figcaption></figure>

{% hint style="info" %}
You have to first deploy a banner to the Commanders Act CDN or on premise location before boing able to link it (see [Deploy Banner](../../user-guides/privacy-banners/deploy-banner.md)).
{% endhint %}

{% hint style="info" %}
All web containers of your website should be re-generated and deployed when installing a new privacy banner.
{% endhint %}

