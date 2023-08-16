---
description: Assign Web Container tags to Consent categories.
---

# Assign Categories

`Data Governance > Consent Management > Categories (tab ASSIGN TAGS)`

Commanders Act TMS tags can be assigned to Consent categories & vendors in following locations.&#x20;

* In `ASSIGN TAGS` tab of `Data Governance > Consent Management > Categories`.&#x20;
* In the `EDIT` tab of TMS Commanders Act.

{% hint style="info" %}
This section is only available in case you use Commanders Act Consent with TMS Commanders Act (Web Container).
{% endhint %}

## Assign categories & vendors in Commanders Act Consent interface

Categories & Vendors are managed separately for each web container. You can select a Web Commander container in the left column. Then you can manage following Consent setting per tag on the right side of the interface.

{% tabs %}
{% tab title="INCLUDE IN PRIVACY SCOPE" %}
This option enables Commanders Act Consent to block a tag depending on a visitors privacy setting.\
\
It is possible to activate or deactivate this setting for all tags via the `all` and `none` buttons on top of the column.
{% endtab %}

{% tab title="CATEGORY" %}
You can assign one Consent category to each tag. This allows visitors to block tags by deactivating the related categories in the privacy center.
{% endtab %}

{% tab title="VENDOR" %}
You can assign one Consent vendor to each tag. This allows visitors to block tags by deactivating the related vendor in the privacy center.
{% endtab %}

{% tab title="BYPASS OPTOUT DEFAULT CONFIGURATION" %}
This option allows you to bypass the default behaviour of tags that are managed with Commanders Act Consent. e.g. Consent will blocks tags that are included in the privacy scope until a visitor provides his consent in case the default account configuration is set to Optout. Bypassing this option would allow you to therefore load tags before the visitor provided his privacy settings (e.g. on the first page). In case such tags are included in the privacy scope they can still be deactivated by the user depending on his privacy settings.

It is possible to activate or deactivate this setting for all tags via the `all` and `none` buttons on top of the column.
{% endtab %}
{% endtabs %}

Additionally you can also manage these Consent settings for following elements:

<figure><img src="../../../../.gitbook/assets/image (207).png" alt=""><figcaption><p>Other elements that can be managed by Commanders Act Consent</p></figcaption></figure>

| Element                                | Description                                                                                                                                                                                                                                                                                      |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **COMMANDERS ACT HITS**                | Commanders Act related hits that are initiated from the container (this includes hits for functionalities like tag deduplication, tag hierarchy, and other). A separate category is available for the cookie sync option. This setting is synced between all client-side TagCommander container. |
| **STATIC AND DYNAMIC JAVASCRIPT CODE** | Custom JavaScript that can be implemented in TagCommander container (found in `ADVANCED` section of the `Edit` tab).                                                                                                                                                                             |

{% hint style="warning" %}
Containers have to be re-generated and deployed to apply these changes.
{% endhint %}

## Assign categories in Commanders Act TMS interface

For convenience it is also possible to directly assign Commanders Act Consent categories & vendors inside the `Edit` tab of TMS Commanders Act (Web Containers). Assigning a category & vendor also includes the tag in the privacy scope.

In case a new vendor is added to the account the tag will not be fired when a user provided an optin for the corresponding category. Therefore it is necessary to activate the "Re-activate privacy" option during the generation of a new banner version to re-ask consent. The option "Don't re-ask the consent to trigger this tag" will change this default behaviour so that the vendor will receive an automatic optin based on the corresponding category.

<figure><img src="../../../../.gitbook/assets/image (184).png" alt=""><figcaption><p>Example: Assigning a Gtag tag to the Analytics category.</p></figcaption></figure>

## IAB TCF V2.2 option

In case you choose to manage tags with IAB 2.2 you do not need to assign IAB compliant tags in the category assignation tab. IAB compliant tags are automatically controlled by the IAB framework.

It is still possible to assign tags to categories to allow Commanders Act Consent to manage them directly with TMS Commanders Act.
