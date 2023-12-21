# Google ACM requires IAB TCF

### New requirement for publishers from 16 January 2024: IAB TCF mandatory

Publishers using Google AdSense, Ad Manager, or AdMob must use a CMP certified by Google and must integrate the IAB’s TCF

{% hint style="info" %}
_In addition to the Google_ [_EU user consent policy_](https://www.google.com/about/company/user-consent-policy/)_, **publishers and developers using Google AdSense, Ad Manager, or AdMob will be required** to use a Consent Management Platform **(CMP) that has been certified by Google and has integrated with the**_ [_**IAB's** Transparency and Consent Framework_](https://iabeurope.eu/transparency-consent-framework/) _(TCF) when serving ads to users in the European Economic Area or the UK._

source: [https://support.google.com/adsense/answer/13554116](https://support.google.com/adsense/answer/13554116)
{% endhint %}

### What needs to be done ? 3 situations

Commanders Act CMP provides you all the keys to be compliant with this new requirement. Depending on your configuration, you’ll fit into one of these use cases:



| Situation #1                                                                      | Situation #2                                                                                                    | Situation #3                                                                                                    |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| <p>You already have</p><p>a TCF privacy banner</p><p>with Google Vendors?<br></p> | You already use an IAB TCF banner template, but you have no Google ACM Vendors?                                 | <p>You don’t </p><p>currently use</p><p>an IAB TCF banner template<br></p>                                      |
| <p>Status: <br><strong>You’re already compliant. Nothing to do</strong><br></p>   | <p>Status: <br>You’re <strong>3 steps away from being compliant.</strong> <br>Follow the instructions below</p> | <p>Status: <br>You’re <strong>4 steps away from being compliant</strong>. <br>Follow the instructions below</p> |

#### Step 1

Go on page: `“Data Governance > Consent Management > Settings”`

* Situation #2: Activate the Google ACM option
* Situation #3: Activate the IAB TCF Compliancy & the Google ACM options

<figure><img src="../../../.gitbook/assets/image (7).png" alt="" width="455"><figcaption></figcaption></figure>

#### Step 2

Go on page: `“Data Governance > Consent Management > Vendors”`

* Situation #2 and #3 : Add your Google ACM Vendors

<div align="center">

<figure><img src="../../../.gitbook/assets/image (8).png" alt="" width="358"><figcaption></figcaption></figure>

</div>

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>



#### Step 3

Go on page: `“Data Governance > Consent Management > Settings”`

* Situation #2: **not required if you already have a TCF privacy banner**\
  **with “Google Advertising Products Vendors”**
* Situation #3: Activate the IAB TCF Compliancy & the Google ACM options

<figure><img src="../../../.gitbook/assets/image (10).png" alt="" width="392"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (11).png" alt="" width="541"><figcaption></figcaption></figure>

#### Final Step

Go on page: `“Sources > Privacy Banners”`

* Situation #2 and #3:\
  • Select your banner, go on tab Generate & Deploy\
  • Generate your new version of the privacy banner\
  It’s ready to be deployed in production!

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
