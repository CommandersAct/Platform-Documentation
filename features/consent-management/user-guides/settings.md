# Settings

`Data Governance > Consent Management > Settings`.

{% hint style="info" %}
Only **administrators** can view and change these account configurations.&#x20;
{% endhint %}

## Account Default Configuration

### Default optout / optin

<figure><img src="../../../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

This setting allows you to handle how tags should be handled in case no consent was yet provided by a user.

{% tabs %}
{% tab title="optout" %}
Your tags are not loaded when a user visits your site. They will be fired when the user continues browsing, unless they refuse cookies beforehand.

**With the General Data Protection Regulation (GDPR), this is the default setting you should choose.**
{% endtab %}

{% tab title="optin" %}
Your tags are loaded when a user visits your site. They are only disabled if the user explicitly refuses cookies.

**This setting is not compatible with the General Data Protection Regulation (GDPR).**
{% endtab %}
{% endtabs %}

{% hint style="info" %}
By default, accounts are configured in optout mode since it is the most popular and is GDPR compliant.
{% endhint %}

### IAB TCF compliancy

This option enables the IAB TCF 2.0 framework for your account. This will enable IAB TCF 2.0 banner, categories and vendors.

### Google Additional Consent Mode

This option enables the [Additional Consent Mode](https://support.google.com/admanager/answer/9681920?hl=en) (ACM) for Google Ad Technology Providers (ATP) for your account. This will enable Google ACM vendor management in the `Categories & Tags` section and extends the IAB TCF API according to the ACM specification.

### Vendor management

This option activates vendors. This will enable vendor management options in the `Categories & Tags` section and enables a vendor management screen in your privacy centers that allows users to manage consent per vendor (requires re-deployment or banners).

## Localisation

This option allows to select country codes (e.g. `fr` for French) that are used to localise the cookie notice of the cookie scanner feature. It is possible to add default country codes by clicking in the white area and selecting a country code from the dropdown. Additionally custom country codes can be added by clicking in the white area and typing the custom country code. The custom country code is saved after pressing `Enter`.

{% hint style="info" %}
It is recommended to use the default country codes listed in the auto-complete dropdown. This allows to localise the cookie notice based on language settings of browsers.
{% endhint %}

## Consent Export Options

See dedicated documentation [here](exports.md).

## Privacy Cookie Name, Separator and Subdomain

These settings allow you to modify the default name, separator and subdomain of your privacy cookie.&#x20;

{% hint style="warning" %}
Changing the cookie name, separator or subdomain can have unwanted side-effects depending on your Commanders Act consent setup. Please contact your Commanders Act consultant or support before applying changes.
{% endhint %}
