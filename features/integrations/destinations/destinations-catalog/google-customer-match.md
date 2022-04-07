# Google Customer Match

Google Customer Match allows you to push users to Google Ads. The matching key is email (SHA-256 or in clear only).

You can create an audience segment, push it to Google Ads and activate it. Users matched could be then activated on Google services (Search, Display network, Gmail, Youtube, Google Shopping...).

## **What are the requirement to sync with Google Ads?** <a href="#what-are-the-requirement-to-sync.-datacommanders-with-google-ads" id="what-are-the-requirement-to-sync.-datacommanders-with-google-ads"></a>

* Sync. key can only be SHA256 email hash in Europe (phone number, mailing address and mobile device ID are for the US)
* Audience size: minimum 1000 matched users (otherwise it will be rejected for privacy purpose)
* Data collection: it is only allowed to import first party data (collected via your website/app/point of sale)
* Available for accounts with good history of policy compliance, good payment history, at least 90 days history, more than USD 50,000 total lifetime spend ([https://support.google.com/google-ads/answer/6299717](https://support.google.com/google-ads/answer/6299717))
* Google indicates that it takes 6 to 12 hours for a list to be populated with members
* A list may appear to be smaller than expected when viewed in the Audience Manager in the Google Ads UI. This view shows the number of _active users_ in the list. A user is considered active if they have recently logged into their Google account.

​[https://developers.google.com/google-ads/api/docs/remarketing/audience-types/customer-match#customer\_match\_considerations](https://developers.google.com/google-ads/api/docs/remarketing/audience-types/customer-match#customer\_match\_considerations)​

## How to configure Google Customer Match connector: <a href="#how-to-configure-google-customer-match-connector" id="how-to-configure-google-customer-match-connector"></a>

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
