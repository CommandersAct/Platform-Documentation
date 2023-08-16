# Manage Categories

`Data Governance > Consent Management > Categories`

In this section you can manage your Commanders Act Consent categories and sub-categories. These categories will be used by your privacy center to provide users with detailed privacy management options.

<figure><img src="../../../../.gitbook/assets/image (213).png" alt=""><figcaption><p>Example: Modal dialogue to create a new category.</p></figcaption></figure>

## Category options

Each Commanders Act Consent category has following options:

| Option                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**                           | Name of the category (e.g. "Analytics", "Advertising", etc.). Privacy centers use this name as the default label for this category in case no localisation was provided in the banner editor.                                                                                                                                                                                                                                                                                                                                      |
| <p></p><p><strong>ID</strong> </p> | ID of the category. This ID is used in raw data exports and for technical setup of certain functionalities. It is possible to manually provide an ID. In case the field is left empty a category ID will be assigned automatically.                                                                                                                                                                                                                                                                                                |
| **Description**                    | Description of the category. Privacy centers use this description as the default description for this category in case no localisation was provided in the banner editor.                                                                                                                                                                                                                                                                                                                                                          |
| **Sub-categories**                 | It is possible to provide sub-categories for each category (e.g. "Universal Analytics", "Matomo", etc. for an "Analytics" category). Each sub-category has a name and an ID. Privacy center use this name as the default label for this sub-category in case no localisation was provided in the banner editor. The ID is used in raw data exports and for technical setup of certain functionalities. It is possible to manually provide an ID. In case the field is left empty a sub-category ID will be assigned automatically. |

## Managing categories

### Default category

In case you use Consent module with TMS Web Container you can select a default category with a drop down on the top left of the interface. New tags in TMS client-side will automatically receive the default category as their privacy category. The default category has a `*` in the category list.

### Creating categories

To add a new category press `ADD CATEGORY` on the the top right of the interface.

### Editing categories

You can edit a Consent category by pressing the `pencil` icon to the right of the category.&#x20;

### Deleting categories

You can delete Consent categories by pressing the `x` icon to the right of the category.

{% hint style="warning" %}
You need to regenerate your consent banners after adjusting pconsent categories. In case you install Consent module with TMS Web Container you will also need to regenerate your Web Container so that your tags have access to the updated categories.
{% endhint %}

## iAB categories

{% hint style="info" %}
Commanders Act Consent module is compliant with IAB TCF 2.2 ([Link to official listing](https://iabeurope.eu/cmp-list/)). To enable IAB categories go to `Data Governance > Consent Management > Settings` and activate the IAB option.\
You can also have a look on [our dedicated page](../../knowledge-base/iab-tcf-v2.2-release-details/)
{% endhint %}

Commanders Act Consent module is compliant with IAB TCF 2.2 ([Link to official listing](https://iabeurope.eu/cmp-list/)) and can use predefined IAB TCF purposes instead of manually configuring categories. Go to `Data Governance > Consent Management > Settings` tab to activate IAB TCF 2.2 option for your account.&#x20;

IAB TCF 2.2 purposes, special purposes, features and special features are automatically added to the `CATEGORIES` tab depending the vendors you add in the `MANAGE VENDORS` tab. You can still add custom categories that you can use side by side with the predefined IAB categories.

The description of IAB TCF 2.2 categories is automatically loaded from the IAB TCF 2.2 framework.

<figure><img src="../../../../.gitbook/assets/image (182).png" alt=""><figcaption><p>IAB purposes are automatically added</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (221).png" alt=""><figcaption><p>Depending of iAB Vendors added</p></figcaption></figure>
