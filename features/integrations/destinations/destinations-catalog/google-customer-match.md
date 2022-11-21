# Google Customer Match

Google Customer Match allows you to push users to Google Ads. Matching keys are email, phone or address (SHA-256 or in clear only).

You can create an audience segment, push it to Google Ads and activate it. Users matched could be then activated on Google services (Search, Display network, Gmail, Youtube, Google Shopping...).

## **What are the requirement to sync with Google Ads?** <a href="#what-are-the-requirement-to-sync.-datacommanders-with-google-ads" id="what-are-the-requirement-to-sync.-datacommanders-with-google-ads"></a>

* Audience size: minimum 1000 matched users (otherwise it will be rejected for privacy purpose)
* Data collection: it is only allowed to import first party data (collected via your website/app/point of sale)
* Available for accounts with good history of policy compliance, good payment history, at least 90 days history, more than USD 50,000 total lifetime spend ([https://support.google.com/google-ads/answer/6299717](https://support.google.com/google-ads/answer/6299717))
* Google indicates that it takes 6 to 12 hours for a list to be populated with members
* A list may appear to be smaller than expected when viewed in the Audience Manager in the Google Ads UI. This view shows the number of _active users_ in the list. A user is considered active if they have recently logged into their Google account.

​[https://developers.google.com/google-ads/api/docs/remarketing/audience-types/customer-match#customer\_match\_considerations](https://developers.google.com/google-ads/api/docs/remarketing/audience-types/customer-match#customer\_match\_considerations)​

## \[New version] How to configure Google Customer Match connector: <a href="#how-to-configure-google-customer-match-connector" id="how-to-configure-google-customer-match-connector"></a>

On the new platform, select Google Customer Match on the destinations catalog.

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-11-21 à 11.07.25.png" alt=""><figcaption></figcaption></figure>

Select All users or one or many segments.

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-11-21 à 11.09.26.png" alt=""><figcaption></figcaption></figure>

### Authentication:

Connect directly to your Google Ads account. Select your existing account if you have already configured it, or configure a new one.

#### New configuration:&#x20;

Click on the link and a new tab will be opened (Connector Credentials).

{% hint style="info" %}
Only admin users have access to the Connector Credentials menu (also available in the Administration menu)
{% endhint %}

On the Connector Credentials page, click on '**Add connector credentials**' and select Google Ads.&#x20;

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-11-18 à 11.44.38.png" alt=""><figcaption></figcaption></figure>

Login to your Google Ads account and the authentication is done.&#x20;

Then go back to the connector configuration page and select the account previously configured.

### Destination configuration

#### Segment mappings

Segments selected will appear in the segment mappings section. You can map here selected segments to a customer list previously created in Google Ads interface (this is where the audience from segments will be sent).&#x20;

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-11-21 à 11.11.59.png" alt=""><figcaption></figcaption></figure>

If you haven't created a customer list yet, you can do it on Google Ads interface:

* On your Google Ads account, click on ‘Tools and settings’ and ‘Audience manager’.
* Then in ‘Audience lists’, click on the + and select ‘Customer list’ (or user list).

#### Mapping User Identifier

In this section, you can define matching keys:

At least:

* Email address: in SHA-256 or plain (we hash it in SHA-256 before to send it)
* and/or Phone number: in SHA-256 or plain (we hash it in SHA-256 before to send it)

Complementary information (optional):

* First name: in SHA-256 or plain (we hash it in SHA-256 before to send it)&#x20;
* Last name: in SHA-256 or plain (we hash it in SHA-256 before to send it)
* Country code (2 letters): in SHA-256 or plain (we hash it in SHA-256 before to send it)
* Postal code: in SHA-256 or plain (we hash it in SHA-256 before to send it)
* Postal address: in SHA-256 or plain (we hash it in SHA-256 before to send it)

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-11-18 à 11.47.49.png" alt=""><figcaption></figcaption></figure>

Last step, simply define a running period and click on Save. The destination will start to send users as soon as they enter in selected segments.

\----------------------------------------------------------------------------------------------------

## \[Old version - deprecated] How to configure Google Customer Match connector: <a href="#how-to-configure-google-customer-match-connector" id="how-to-configure-google-customer-match-connector"></a>

{% hint style="info" %}
Method available only on the old platform, if you haven't migrated yet. \
Please note this version only support email (SHA-256 or plain) as matching key.
{% endhint %}

### **Google Ads customer ID** <a href="#google-ads-customer-id" id="google-ads-customer-id"></a>

First, you need to enter your Google Ads customer ID:

{% embed url="https://support.google.com/google-ads/answer/1704344?hl=en" %}

![](https://2406699966-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-MZSeafT12AfKYHgDcYB%2F-MZSfZgMyAes\_J7i0FBE%2Fimage.png?alt=media\&token=8ff94c10-a6b5-408c-bd73-ca0111ceec4e)

### Grant access <a href="#grant-access" id="grant-access"></a>

Then, there are 2 ways to configure it:

#### Option 1- 'I have already granted Commanders Act access to my Google Ads account' <a href="#option-1-i-have-already-granted-commanders-act-access-to-my-google-ads-account" id="option-1-i-have-already-granted-commanders-act-access-to-my-google-ads-account"></a>

It is the fastest and easiest way to configure the connector. Simply ask our consultants or customer representative that you want to use this option and provide them your Google Ads Customer ID. Then they will link your account with our Google Ads account in order to be able to push audiences.

#### Option 2- 'I provide my own authentication tokens' (not recommended) <a href="#option-2-i-provide-my-own-authentication-tokens-not-recommended" id="option-2-i-provide-my-own-authentication-tokens-not-recommended"></a>

We recommend using the first option, as the second option is much more complex and requires access to Google Developer Console. You have to enter the Developer Token, Client ID, Client Secret and generate a refresh token.

All details here:

{% embed url="https://developers.google.com/adwords/api/docs/guides/first-api-call#configuration_elements" %}

### Create a user list on Google Ads <a href="#create-a-user-list-on-google-ads" id="create-a-user-list-on-google-ads"></a>

Last step, create a user list on Google side.

* On your Google Ads account, click on ‘Tools and settings’ and ‘Audience manager’.
* Then in ‘Audience lists’, click on the + and select ‘Customer list’ (or user list).
* Create the list, save it, open it and find the List ID
* Paste the List ID in the segment mappings on the Data Commander Google Customer Match connector interface (it allows you to map a segment in DataCommander to a user list on Google Ads)
* Your connector is ready, click save

After 12 to 24 hours, go back to Google Ads, click on your customer list you created just before, and it will be filled with users selected.​
