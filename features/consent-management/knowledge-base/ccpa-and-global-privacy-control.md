# CCPA & Global Privacy control

## Introduction to CCPA

The [California Consumer Privacy Act of 2018](http://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?division=3.\&part=4.\&lawCode=CIV\&title=1.81.5) (CCPA) gives consumers more control over the personal information that businesses collect about them and the [CCPA regulations](https://govt.westlaw.com/calregs/Browse/Home/California/CaliforniaCodeofRegulations?guid=I5E53FC80FEDE11ECA3A49C17D1AA5D7C\&originationContext=documenttoc\&transitionType=Default\&contextData=\(sc.Default\)) provide guidance on how to implement the law. This landmark law secures new privacy rights for California consumers, including:

* The [right to know](https://oag.ca.gov/privacy/ccpa#sectionc) about the personal information a business collects about them and how it is used and shared;
* The [right to delete](https://oag.ca.gov/privacy/ccpa#sectiond) personal information collected from them (with some exceptions);
* The [right to opt-out](https://oag.ca.gov/privacy/ccpa#sectionb) of the sale or sharing of their personal information; and
* The [right to non-discrimination](https://oag.ca.gov/privacy/ccpa#sectiong) for exercising their CCPA rights.

In November of 2020, California voters approved [Proposition 24, the CPRA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?division=3.\&part=4.\&lawCode=CIV\&title=1.81.5), which amended the CCPA and added new additional privacy protections that began on January 1, 2023. As of January 1, 2023, consumers have new rights in addition to those above, such as:

* The [right to correct](https://oag.ca.gov/privacy/ccpa#sectione) inaccurate personal information that a business has about them; and
* The [right to limit](https://oag.ca.gov/privacy/ccpa#sectionf) the use and disclosure of sensitive personal information collected about them.

[Businesses](https://oag.ca.gov/privacy/ccpa#sectiona) that are subject to the CCPA have several responsibilities, including responding to consumer requests to exercise these rights and giving consumers certain [notices explaining their privacy practices](https://oag.ca.gov/privacy/ccpa#sectiond). The CCPA applies to many businesses, including [data brokers](https://oag.ca.gov/privacy/ccpa#sectiong).

### Changes for CCPA in 2023 due to CPRA

It is required under CPRA to retain a minimum amount of data that is only essential for the organization to fulfill its requirements. In addition, businesses should not keep data for longer than necessary; if they do, a justification must be presented, and they must notify the user. The criteria to Comply with CPRA remained almost the same as in CCPA, but with a slight change:

1. Businesses should comply if they obtain a revenue of more than $25 million or gain 50% from selling personal data.
2. Businesses should comply if they process data of more than 100,000 users instead of 50,000.

The **California Privacy Protection Agency** was created to enforce the CPRA starting **July 1, 2023.** It is responsible for raising awareness about data privacy and ensuring that consumers’ rights are protected while implementing penalties on non-compliant entities.

{% hint style="info" %}
For more information, please visit the official CCPA website\
[https://oag.ca.gov/privacy/ccpa](https://oag.ca.gov/privacy/ccpa)
{% endhint %}

## As a Commanders Act customer, what should I'm supposed to do?

To to be compliant with CCPA, simply follow these steps:

1.  Create a dedicated ccpa banner: use the "**footer with privacy center" template**\


    * Add your text about cookies: must list the categories of personal information businesses collect about consumers and the purposes for which they use the categories of information. Don't forget to integrate a **link for your cookie policy.**
    * Add a button with this exact text : “**Do Not Sell My Personal Information”**\
      This button should Optout the user (value refuse all)  **or** open a privacy center with one category “**Personalized advertisement**”. \
      Please note: this category is a requirement (must contains all tags that can sell personal information).
    * Set your [consent duration](../user-guides/settings.md) for at least **12 months**&#x20;


2.  **Enable the** [**Global Privacy Control**](ccpa-and-global-privacy-control.md#how-enable-the-global-privacy-control) option on your Commanders Act privacy banner\


    <figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="320"><figcaption></figcaption></figure>
3. Integrate in your website footer a **link or a button to manage consent choices**\
   example of html code to integrate:\
   `<a href="#" onclick="tC.privacyCenter.showPrivacyCenter();return false">privacy center</a>`&#x20;
4. **Update your Privacy Policy:**\
   Businesses that sell personal information about California residents, or allow information to be collected on their websites or apps, need to provide information in their privacy policies about that collection or sale. The CA Attorney General has provided draft regulations on how and what information should be included in privacy policies, which you can find [here](https://oag.ca.gov/sites/all/files/agweb/pdfs/privacy/ccpa-proposed-regs.pdf).
5.  **Add file "well-known.json" on your site**\
    Not mandatory, but recommended, GPC makes use of .well-known identifiers for sites to signal compliance with the    &#x20;GPC specification. The existence of this file indicates you are using GPC as part of your compliance&#x20;    &#x20;with privacy laws. \
    There may be a variety of tools available to implement the .well-known file on your site.\


    The following is a basic example of how to specify a static folder and files for your site.\


    First, create a folder called .well-known at the root of your site, so that the path is yoursite.com/.well-known/. Within this folder, create a file called gpc.json. The value of the file should then look something like this, with `lastUpdate` set to the date you last updated the file.\
    `{`    \
    `"gpc": true,`    \
    `"lastUpdate": "2025-04-20"`    \
    `}`\
    \
    This will give you a valid GPC file which states that you comply with the GPC in the context in which you understand it.\
    Adopters will usually supplement the .well-known file with a statement in their privacy policy that explains exactly how they interpret the GPC within their own systems. The exact message in your privacy policy is up to you and may require review by your legal team.

## What is Global Privacy Control ?

The Global Privacy Control is an initiative aimed at enabling users to easily exercise their privacy preferences across multiple websites and online services. It is designed to give users more control over how their personal information is collected, used, and shared online.

The GPC operates through a browser signal or an HTTP header that users can activate to indicate their privacy preferences. When a user enables the GPC signal in their browser, it sends a request to websites and online services, indicating that the user wishes to opt out of the sale or sharing of their personal information.

For more information, you can visit their [website](https://globalprivacycontrol.org/)

## How to enable the Global Privacy Control ?

Simply follow these 2 easy steps:

1 - Enable on the option Global Privacy Control directly on your CCPA Banner&#x20;

```
Sources > Privacy Banners > Settings
```

\
2- Regenerate and Deploy your Consent Banner

<figure><img src="../../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>

```
Sources > Privacy Banners > Generate
```

3 - Verify your setup! You can use a [dedicated GPC plugin](https://app.gitbook.com/s/nrgRgmj0gYZXv84bLI9l/basic/destinations/gamned/description) to check your implementation\


<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>
