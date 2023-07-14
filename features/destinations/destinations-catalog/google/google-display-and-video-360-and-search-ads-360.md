# Google Display & Video 360 & Search Ads 360

[Google ](https://about.google/)is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software.\
Google Display & Video 360 and Google Search Ads 360 are paid products part of [Google Marketing Platform](https://marketingplatform.google.com/about/).

![](<../../../../.gitbook/assets/image (3) (1) (1) (1) (1).png>)

## First step: <a href="#googleddpsetup-firststep" id="googleddpsetup-firststep"></a>

Ensure that you already have a Google Marketing Platform account (360).

Contact your Google Account Manager to whitelist our DMP + get your Client ID (Client Customer ID: Your DoubleClick Client Customer ID)

{% hint style="danger" %}
* **We are listed as "TagCommander" and not as "Commanders Act".**
* **You have to ask for the whitelisting of the advertiser ID, as we don't currently use the Partner ID on our connector.**
{% endhint %}

{% hint style="danger" %}
This connector is **only for Google DV360 accounts** (including Google Ads for DV360) but not for Google Ads accounts (without a DV360 account).

If you have a Google Ads account, you can use the Customer Match connector or RLSA (Remarketing Lists for Search Ads).
{% endhint %}

Example of answer from [dv360-support@google.com](mailto:dv360-support@google.com):

_“You just have to tell your Google account manager to raise a DMP whitelisting request and once we receive that request it would be a new ticket altogether. So, one of our agents would be able to look into that and process your request.”_

References:

* Google Ads : [https://developers.google.com/third-party-ads/googleads-vendors](https://developers.google.com/third-party-ads/googleads-vendors) (look for "Fjord Technologies SAS")
* Ad Manager : [https://developers.google.com/third-party-ads/adx-vendors](https://developers.google.com/third-party-ads/adx-vendors) (look for "Fjord Technologies SAS")
* Ad Manager & Ad Exchange: [https://support.google.com/admanager/answer/9012903](https://support.google.com/admanager/answer/9012903) ("look for Commanders Act")
* Youtube : the partners' program has been closed

## Step 2:

Wait for Google to whitelist our DMP.

## Step 3 - Select your connector <a href="#googleddpsetup-step3-pickyourconnector" id="googleddpsetup-step3-pickyourconnector"></a>

* Display & Video 360 was previously DoubleClick Bid Manager.
  * If you had a DoubleClick Bid Manager account or if you have a Display & Video 360 account, please use our connector 'Google Display & Video 360 Bid Manager'
* Search Ads 360 was previously DoubleClick Search.
  * If you had a DoubleClick Search account or if you have a Search Ads 360 account, please use our connector 'Google Search Ads 360'
* Display & Video 360 can be also used with an Adexchange account
  * If you had an Adexchange account, please use our connector 'Google Display & Video 360 Adex'

### Errors you can encountered with the connector:

* \[Google DDP API]\[2473] Could not fetch lists: \[AuthorizationError.**USER\_PERMISSION\_DENIED** @ clientCustomerId]

→ Trouble with the whitelisting: be sure you are using the right name (TagCommander) and the right ID (advertiser ID).

* \[Google DDP API]\[3206] Could not fetch lists: \[DmpUserListServiceError.**INVALID\_CLIENT\_CUSTOMER\_ID** @ clientCustomerId]

→ You don't have a Google DV360 account. Please use the Customer Match connector or RLSA (Remarketing Lists for Search Ads)

## Step 4 - Create your stream <a href="#googleddpsetup-step4" id="googleddpsetup-step4"></a>

Pick your segment and create your stream

\+ Put Google Client ID, if you do not have it, then it fails

Segments will be directly created by Commanders Act, and will appear in the Audience list in Google Ads.

Interface of DV360 where you are supposed to find the segments:

![](https://lh3.googleusercontent.com/7Y864jfrb3kvgMNGME5BNh5n5GX9g6os4AmR-En8MK1LGamxEwJxROOt93G18iEBMQ)

{% hint style="info" %}
The sharing is based on a cookie synchronization between Commanders Act and Google. If you see less data than expected in the data stream, check your cookie-sync ratio.
{% endhint %}
