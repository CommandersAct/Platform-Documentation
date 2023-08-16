# ATT - App Tracking Transparency (iOS 14.5+)

Since April 2021, Apple requires that your app provide a transparency popup to ask user permission for tracking, beginning with iOS 14.5 () and the [ATT framework](https://developer.apple.com/app-store/user-privacy-and-data-use/).![](https://2406699966-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-Lh69-tfWlhrtYE5Vhvq%2F-MaiF-w24SWv5y8SOIMW%2F-MaiGjF-iT3r253c4x3p%2Fimage.png?alt=media\&token=8dd6783b-70cb-4116-9cd8-74becdea30a7)

### When and how should you request permission from the ATT?  <a href="#when-and-how-should-you-request-permission-from-the-att" id="when-and-how-should-you-request-permission-from-the-att"></a>

Before attempting to use the IDFA from an iOS device, you must first display the ATT tracking permission alert, according to Apple's guidelines. If permission is not requested or if the user declines, the IDFA will be unavailable to your app and any embedded third-party SDKs. Third-party SDKs may not function properly in this case.To really complies with both Apple and GDPR requirements, you must open the ATT popup to get user permission **as well** as open CMP popup to get user consent for GDPR purpose. ATT isn't currently compliant with the IAB TCF or with GDPR prerequisites, so it can't be utilized as the lone consent collection system and should be utilized with the Commanders Act CMP.

### Our recommended solutions <a href="#our-recommended-solutions" id="our-recommended-solutions"></a>

#### 1. Most accepted solution : ATT first <a href="#1.-most-accepted-solution-att-first" id="1.-most-accepted-solution-att-first"></a>

From customer's experiences, the **most accepted solution** by Apple is to :

1. Open the ATT popin
2. Depending of user's choice on ATT :
   1. if the user choose to allow the tracking, then open the TrustCommander popin to collect the consent
   2. If the user refuse the tracking in the ATT popin, the user has to be considered as optout **without** opening the TrustCommander popin

#### 2. ATT after Commanders Act Consent banner <a href="#2.-att-after-trustcommander" id="2.-att-after-trustcommander"></a>

For some customer's this solution worked also :

1. Open the Commanders Act Consent popin
2. **Whatever the consent**, open the ATT popin just after

{% hint style="info" %}
This setup offers the advantage of allowing the user to consent certain purposes whatever his choice regarding the popin ATT tracking. Neverthe less this implementation is some time refused by some Apple reviewers
{% endhint %}

To go further, here a for France customers the position of the competition authority on this subject: [https://www.autoritedelaconcurrence.fr/fr/communiques-de-presse/ciblage-publicitairemise-en-place-par-apple-de-la-sollicitation-att-lautorite](https://www.autoritedelaconcurrence.fr/fr/communiques-de-presse/ciblage-publicitairemise-en-place-par-apple-de-la-sollicitation-att-lautorite)
