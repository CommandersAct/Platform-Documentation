# Manage Banner

## Manage Banner

Options to create and edit banner templates.`Sources > Privacy banners`

### Creating Privacy Banner <a href="#creating-privacy-banner" id="creating-privacy-banner"></a>

Click `ADD PRIVACY BANNER` in the top right of the interface to add a new banner to your account. Each template has following options:

| Field                          | Description                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**                       | Label of the banner used in the interface.                                                                                                                                                                                                                                                                                                                                                        |
| **Template**                   | Dropdown to select a template for this banner.                                                                                                                                                                                                                                                                                                                                                    |
| **Hosting**                    | Hosting method used for this banner (see [Deploy Banner](deploy-banner.md)).                                                                                                                                                                                                                                                                                                                      |
| **Consent duration**           | Duration how long the consent cookie is valid. After this duration the consent cookie is not valid anymore and a new banner will be presented to the user. It is possible to configure a duration in full months between 1 and 13 month. This has no impact on the storage duration of the consent in the Commanders Act Consent database.                                                        |
| **Use the new privacy center** | This option allows to use the old privacy center template of Commanders Act Consent Banners. This option allows to use custom CSS and custom JS that was created for old banner templates. In case you are not sure if a banner was customized please check with your Commanders Act consultant or support contact before creating a new template. This option is not available on all templates. |

Example: Configuring options of a privacy banner.

<figure><img src="../../../../.gitbook/assets/image (198).png" alt="" width="455"><figcaption></figcaption></figure>

### **Update Privacy Banner** <a href="#update-privacy-banner" id="update-privacy-banner"></a>

You can open and edit the privacy banner settings via the `gear` icon on the top left of the interface.

{% hint style="warning" %}
Changing banner templates might not work for customized privacy banner templates. Please contact your Commanders Act consultant or support in case you are unsure if your banner was customized before using this option.
{% endhint %}



<figure><img src="../../../../.gitbook/assets/image (216).png" alt=""><figcaption></figcaption></figure>

### Customize banner content <a href="#customise-banner-content" id="customise-banner-content"></a>

`Sources > Privacy banners (tab EDIT BANNER)`

#### Options for banner customization <a href="#options-for-banner-customisation" id="options-for-banner-customisation"></a>

All banner templates can be customized with a WYSIWYG editor. Following options are available for all banners (except IAB TCF and Popin with Categories templates).

{% tabs %}
{% tab title="CONTENT" %}
Options to manage the main text content of your banner.

* Content: Text content (supports HTML formatting and links).
* Font color: Text color.
* Background color: Background color of the content area.
{% endtab %}

{% tab title="BUTTON" %}
Options to manage up to three buttons.

* Label: Button text.
* Font color: Color of the button text.
* Background color: Background color of the button.
* Button action: Action the button performs (e.g. optin to all categories or open privacy center).
* Button Position: Change Button Position to Top/Bottom of the banner. Only one button can be positioned to top.
{% endtab %}

{% tab title="CUSTOM CSS" %}
Custom CSS that can be used by advanced users to customise the banner style. **This CSS is applied globally to your website, avoid to use global selectors and use the HTML ID attribute of the banner elements instead.**
{% endtab %}

{% tab title="CUSTOM JS" %}
Advanced customization options. Please contact your Commanders Act consultant or support before using these.
{% endtab %}
{% endtabs %}

Changes have to be saved with the `SAVE` button.

#### Options for privacy center customization <a href="#options-for-privacy-center-customisation" id="options-for-privacy-center-customisation"></a>

Following options are available for the privacy center and "Popin with categories" templates.



{% tabs %}
{% tab title="HEADER" %}
Options to manage the header text of your privacy center.

* Title: Text content.
* Font color: Text color.
* Background color: Background color of the header area.
{% endtab %}

{% tab title="CONTENT" %}
Options to manage the main text content of your banner.

* Categories introduction: Introductory text of the category tab (supports HTML formatting and links)
* Vendors introduction: Introductory text of the vendor tab  (supports HTML formatting and links, only visible in case IAB TCF 2.0 or custom vendors were activated)
* Font color: Text color.
* Background color: Background color of the content area.
{% endtab %}

{% tab title="CATEGORIES" %}
Options to manage the privacy categories of the privacy center. These categories are based on the categories managed in the `Categories & Tags` part of the interface.

* Order: Drag and Drop sorting of Categories.
*   `edit` icon that allows to overwrite the default name and description of categories and sub-categories that have been provided in the&#x20;

    `Categories & Tags` section of the interface for this banner (used for localisation).
* Checkbox that allows to hide a category (below `edit` icon).
* Categories Blocked On: Checkbox that permanently enables a category that can not be deactivated by visitors (e.g. for an "essential cookies" category)
* _IAB TCF 2.0 option:_  IAB purposes, special purposes, features and special features are automatically displayed on the basis of selected vendors in `Categories & Tags / Manage vendors`section. The categories translation is done automatically depending on the user’s browser language settings. Non-IAB categories will be displayed after the official IAB categories in the banner.
{% endtab %}

{% tab title="VENDORS" %}
Options to manage and translate descriptions of custom vendors. IAB TCF 2.0 vendor descriptions and translations are managed automatically by the IAB TCF 2.0 framework.

* Vendor Description: Description displayed in the vendor tab.
* Hide Vendor: Options to hide the vendor from the banner.
* Order of vendors can be changed via drag & drop. (IAB TCF 2.0 vendors are always displayed before custom vendors).
{% endtab %}

{% tab title="BUTTONS" %}
Custom CSS that can be used by advanced users to customise the banner style.Options to manage the save button, and the category controls of the privacy center.

* Label: Button text.
* Font color: Color of the button text.
* Background color: Background color of the button.
* Default status of buttons (IAB and non-IAB) to accept or refuse categories and sub-categories:
  * "On": "On" is chosen by default for categories/sub-categories (IAB and non-IAB) in the Privacy Center. When the visitor leaves it as such, their status for browsing is “optin”.
  * "Off": "Off" is chosen by default for categories/sub-categories in the Privacy Center. When the visitor leaves it as such, their status for browsing is “optout”.
  * "Neutral position": In this position, neither "On" nor "Off" is chosen by default for categories/sub-categories in the Privacy Center. The user must choose “On” or “Off” for each of the categories and sub-categories to be able to save their preferences and continue browsing. The “Warning message” field allows you to personalise the message that will appear to the left of the save button in the Privacy Center: this will inform the user that they must give or refuse their consent for all the categories before saving.
* Default status of buttons to accept or refuse vendors (IAB and non-IAB):
  * "Off": The default status of vendors is "Off". When a new visitor accepts consent categories in the privacy center for the first time the vendors are not not activated based on their linked categories.
  * "Neutral position": The default status of vendors is "Undecided". When a new visitor accepts consent categories in the privacy center for the first time the vendors activate based on their linked categories (see [Manage Vendors](../categories-and-tags/manage-vendors.md)).
* Label for "Off for all": "Off for all" button text if the user wants to give their choice for all of a category’s sub-categories in one click.
* Label for "Off" button: "Off" button text which appears in the Privacy Center (e.g. you can replace it by “No”).
* Label for "On for all": "On for all" button text if the user wants to give their choice for all of a category’s sub-categories in one click.
* Label for "On" button: "On" button text which appears in the Privacy Center (e.g. you can replace it by “Yes”).
* "ON blocked" look & feel: Styling of on blocked Categories (Checkbox or Text)
{% endtab %}

{% tab title="CUSTOM CSS" %}
Custom CSS that can be used by advanced users to customise the banner style.
{% endtab %}

{% tab title="CUSTOM JS" %}
Advanced customisation options. Please contact your Commanders Act consultant or support before using these.
{% endtab %}
{% endtabs %}

Changes have to be saved with the `SAVE` button.

### Advanced Options for IAB TCF Banner <a href="#advanced-options-for-iab-tcf-banner" id="advanced-options-for-iab-tcf-banner"></a>

#### Customise Publisher Country Code Field <a href="#customise-publisher-country-code-field" id="customise-publisher-country-code-field"></a>

Option to manage the `publisherCC` field of the IAB TCF API.

​[Country code](https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-2#Officially\_assigned\_code\_elements) of the country that determines the legislation of reference. Normally corresponds to the country code of the country in which the publisher's business entity is established.\


Consent banners sets this value to `"FR"` by default in the IAB response. The publisher country code field can be customised with following JavaScript snippet (should be implemented in the first container on the website.).

`tC.privacy.iabPublisherCC = "<country_code>";`

Example to set the publisher country code field to a German country code:

`tC.privacy.iabPublisherCC = "DE";`

#### Customise Purpose One Treatment Field <a href="#customise-purpose-one-treatment-field" id="customise-purpose-one-treatment-field"></a>

Option to manage the `purposeOneTreatment` field of the IAB TCF API.

IAB TCF offers this field to specify how purpose one should be treated in specific scenarios.

**true:** Purpose 1 not disclosed at all. CMPs use publisherCC to indicate the publisher's country of establishment to help Vendors determine whether the vendor requires Purpose 1 consent.

**false:** There is no special Purpose 1 treatment status. Purpose 1 was disclosed normally (consent) as expected by TCF Policy

Consent banner sets this value to `false` by default in the IAB response. The purpose one treatment field can be customised with following JavaScript snippet (should be implemented in the first container on the website.).

`tC.privacy.iabPublisherCC = (true|false);`

#### Neutral vendor buttons <a href="#neutral-vendor-buttons" id="neutral-vendor-buttons"></a>

You can change the vendor button type to neutral if you choose the neutral position as the default status.f

<figure><img src="https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-Lh69-tfWlhrtYE5Vhvq%2F-MEgUShTWffyLFmt-ou8%2F-MEgUtHEbE82gQ_S5bqE%2Fimage.png?alt=media&#x26;token=618886af-dc23-4685-a1a4-f6690ba6e87b" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="info" %}
You can't choose a neutral position for IAB categories (purposes) as it's not allowed by the framework policy
{% endhint %}

#### Synchronization mode between vendors and categories <a href="#synchronisation-mode-between-vendors-and-categories" id="synchronisation-mode-between-vendors-and-categories"></a>

You can choose to synchronize vendors status with categories, choosing to do it only for neutral buttons or always. If you use an IAB TCF template, this option will not have any effects on TCF vendors, as the TCF framework doesn't allow this.

<figure><img src="https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-Lh69-tfWlhrtYE5Vhvq%2F-MY5SiojbBrAG06J3ozc%2F-MY5UR0Z4-RqTYfR0jAW%2Fimage.png?alt=media&#x26;token=461c6466-faf8-40be-98db-7bf3f920a7f8" alt="" width="563"><figcaption></figcaption></figure>

#### IAB TCF Stacks `Beta` <a href="#iab-tcf-stacks-beta" id="iab-tcf-stacks-beta"></a>

Commanders Act Consent offers IAB TCF Stacks to reduce the size of the purpose list in the privacy center. IAB TCF Stacks group purposes and special features in a foldable panel and allows visitors to configure consent for all purposes and special feature in a Stack at once. More information on IAB TCF Stacks can be found in the [IAB TCF Policy](https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/#\_\_\_E\_Stacks\_\_).

Right now IAB TCF Stacks are in beta in Commanders Act Consent. They are activated with a JavaScript command that needs to be added to the privacy center `CUSTOM JS` field `JS BLOCK BEFORE`.Example: Activating Auto Stacks

<figure><img src="https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-Lh69-tfWlhrtYE5Vhvq%2F-MB99zvC3zSePd1mqFI_%2F-MB9H71v7JlA2x9WEi8i%2FIAB%20Stack%20Activation.png?alt=media&#x26;token=026c7224-3d88-4928-a53d-640854a34adf" alt="" width="375"><figcaption></figcaption></figure>

Commanders Act Consent offers two options to activate Stacks:

{% tabs %}
{% tab title="Auto Stacks" %}
```
pc.iab.useAutoStack();
```

This option uses an algorithm to automatically find the tightest Stack combination for the configured vendors. This option is the recommended approach.
{% endtab %}

{% tab title="Manual Stacks" %}
```javascript
pc.iab.useStackIds(1,2); // activates Stacks with ID 1 and 2
```

This option allows to manually activate IAB TCF Stacks by providing a list of Stack IDs. The Stack IDs can be found in the [IAB TCF Policy](https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/#\_\_\_E\_Stacks\_\_).

{% hint style="warning" %}
Purposes may only be included in one Stack. In case of a bad configuration Commanders Act Consent ignores IAB Stack configuration and provides an error in the browser console.
{% endhint %}
{% endtab %}
{% endtabs %}



#### Move native Categories above IAB Purposes <a href="#move-native-categories-above-iab-purposes" id="move-native-categories-above-iab-purposes"></a>

Per default IAB Purpose controls are placed above native category controls. It is possible to display native categories above IAB TCF Purpose controls by adding following JavaScript snippet to the `CUSTOM JS` field `JS BLOCK BEFORE` of the privacy center.

`pc.tc.categoriesSectionTop(true);`

The "Other" headline of the native category controls can be translated by adding following configuration snippet to the `CUSTOM JS` field `JS BLOCK BEFORE` of the privacy center.

`pc.addTranslation({en: { others: 'My Headline' }});pc.setLocale('en');`
