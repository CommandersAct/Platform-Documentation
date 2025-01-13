# Accessibility Template

## WCAG standards : offer a privacy fully functional for people with disabilities



Among the available templates, one is dedicated to accessibility. It ensures compatibility with RGAA and WCAG 2.0 level AA standards.

<figure><img src="../../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Web Content Accessibility Guidelines (WCAG) is developed through the [W3C process](https://www.w3.org/WAI/standards-guidelines/w3c-process/) in cooperation with individuals and organizations around the world, with a goal of providing a single shared standard for web content accessibility that meets the needs of individuals, organizations, and governments internationally.

More information here : [https://www.w3.org/WAI/standards-guidelines/wcag/](https://www.w3.org/WAI/standards-guidelines/wcag/)

## **What is Web Accessibility ?**

When websites and web tools are properly designed and coded, people with disabilities can use them. However, currently many sites and tools are developed with accessibility barriers that make them difficult or impossible for some people to use.

Making the web accessible benefits individuals, businesses, and society. International web standards define what is needed for accessibility.

Web accessibility means that websites, tools, and technologies are designed and developed so that people with disabilities can use them. More specifically, people can:

* perceive, understand, navigate, and interact with the Web
* contribute to the Web

With this template the main key point is to offer a privacy fully functional for people with disabilities.

## Translation

The Accessibility template provides an automatic translation of different labels. This translation is based on navigator language.\
Currently, it supports : Italian, English, German, French and Russian.

## Options :

### 1. Personalize translation

Banners

You can either add new translation or override aria labels by using the function `tC.privacy.addTranslation()` in the custom JS.

Labels available :

`iframeTitle` : Title attribute of the iframe

`privacyLabel` : Aria Label of the footer

`acceptAria` : Aria Label of the accept button

`refuseAria` : Aria Label of the refuse button

`showPcAria` : Aria Label of the “Show Privacy Center“ Button

Exemple :

```javascript
tC.privacy.addTranslation({
  en : {
    // overriding
    iframeTitle : 'the iframe title you want',
    privacyLabel : 'the aria label you want',
    acceptAria: 'the aria label you want for accept button',
    refuseAria: 'the aria label you want for refuse button',
    showPcAria: 'the aria label you want for display the pc button'
  },
  ru: {
    // add new translation
    iframeTitle : 'the iframe title you want',
    privacyLabel : 'the aria label you want',
    acceptAria: 'the aria label you want for accept button',
    refuseAria: 'the aria label you want for refuse button',
    showPcAria: 'the aria label you want for display the pc button'
  }
})
```

**Privacy Center**

**⚠️** To translate the privacy you must use another function: `pc.addTranslation()`

Available keys and their values :

```javascript
var en = {
    "pcAria":"Cookie settings",
    "closePrivacyCenter":"Close the cookie setting dialog",
    "acceptAll":"Accept all",
    "refuseAll":"Refuse all",
    "saveLabel":"Save",
    "saveAria":"Save the current cookie settings",
    "acceptAllAria":"Accept all cookies",
    "refuseAllAria":"Refuse all cookies",
    "showVendors":"Show vendors",
    "showPurposes":"Show purposes",
    "vendors":"Vendors",
    "enableCookieLabel":"Enabled:",
    "enableCookieAria":"{label} cookies enabled",
    "disableCookieAria":"{label} disabled cookies",
    "turnOnSubCategoriesAria":"Enable {label} cookies",
    "turnOffSubCategoriesAria":"Disable {label} cookies",
    "cookieAlwaysOnSrPrefix":"",
    "cookieAlwaysOnSrSuffix":"",
    "cookieSrPrefix":"",
    "cookieSrSuffix":"",
    "showRelatedVendors":"Show related vendors",
    "privacyPolicy":"Privacy policy",
    "categories":"Categories"
}
```

Some of the translation accept a label as {label}. The label here is always the label of the category.

The last keys with `SrPrefix`/`SrSuffix` have empty translation by default. These keys are used for “sr-only” text which are prefixing and suffixing the category name. These text are only readable by a screen reader.

`cookieSr` are used when the category isn’t locked

`cookieAlwaysOnSr` replaces `cookieSr` if the category is blocked to on

Example:&#x20;

```javascript
pc.addTranslation({
  en : {
    // Override english Aria Label
    closePrivacyCenter: 'Close the privacy center', 

  },
  ru : {
    // you can also add a new language
    closePrivacyCenter: 'Close the privacy center',
      },
})
```

### 2. Force Translation

By default, texts provided to screen readers is translated depending on the navigator language.\
In some case you may want to display a privacy in english for example even if the navigator language is another one. ie : with an ISO language code in the url

You can force the privacy to take a language by using the function setLocale in the Privacy Center > Custom JS field > JS Block Before :

```javascript
pc.setLocale("fr");
```

> Value can be : fr, it, de, ru or en

Note : this function must be placed after the translation declaration.

### 3. Focus Trap

The focus trap is an accessibility option designed so that keyboard user have their navigation locked to the banner. Pressing the TAB key would cycle between the different navigation elements of the banner without going on your website. This is an accessibility recommendation when using modal on a webpage.

You can deactivate the focus trap by adding the following JavaScript snippet to the custom JS of the accessibility template banner:

```javascript
tC.privacy.enableFocusTrap(false);
```

