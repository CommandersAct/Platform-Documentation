# Consent Mode in Commanders Act CMP

## Introduction

Google Consent Mode will evolve in March 2024!&#x20;

As Google strongly recommends the use of Consent Mode on their tags, Commanders Act has developed a new built-in feature for clients who wish to implement it.

Just use our new native feature for a super smooth implementation!\
\
Please read the following documentation to learn more about this new feature, and how to use it.\
\
If you have already implemented Consent Mode v1 using our tag template and would like to keep it, you can update it on v2. Please see the following section for instructions: [Migration Guide Consent Mode v1 tag template to v2](consent-mode-in-commanders-act-tms.md#migration-guide)

## Difference between Basic & Advanced mode

Google Consent Mode provides 2 approaches: Basic & Advanced\
In both cases, you will have to activate the feature Google Consent Mode on your account.\
The only difference will be the following:\
\
**Basic Mode:** Google tags aren't triggered before consent & remains submitted to Commanders Act Consent Rules, there will be no tags firing in case of Optout\
**Advanced Mode:** Google tags are triggered before consent & the collected data will depend on the Consent Mode Signal. Tags remains fired even when user has Optout.

## How to use the Google Consent Mode feature ?

Just follow these 6 steps:

### 1- Activate the feature on your workspace

Login on[ your workspace ](https://app.commandersact.com/)\
Go on page `Data Governance > Consent Management > Settings`\
Turn **On** the option Google Consent Mode. The sub-menu "Google Consent Mode settings" will appears

<figure><img src="../../../../.gitbook/assets/image (484).png" alt=""><figcaption></figcaption></figure>

### 2-Configure your settings

#### Categories

Select your appropriate Privacy category from the drop-down list for each Google's category.

<figure><img src="../../../../.gitbook/assets/image (485).png" alt=""><figcaption></figcaption></figure>

#### Default Status

The Default Status will determine the behaviour of your tags BEFORE consent. \
If set on "denied": Google will collect minimum information (as if the user has Optout)\
If set on "granted": Google will collect all information (as if the user has Optin)\
\*You should ask to your DPO before to set a "granted" default status for any of theses categories

In all cases: once the user has given his consent (optin or optout), the default status will no longer apply. The user's choice will determine the status after consent.

<figure><img src="../../../../.gitbook/assets/image (486).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
If you do not set a category, the status will always be "denied". \
The "Default Status" dropdown menu will no longer be displayed. \
Example below for "security\_storage" with no privacy category assigned:
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (465).png" alt=""><figcaption></figcaption></figure>

#### Additional Settings

*   **enable\_tcf\_support**\
    Enable the feature [tcf\_support](https://developers.google.com/tag-platform/security/guides/implement-TCF-strings?hl=en#implementation) to let your IAB TCF privacy banner manage the advertising categories.\


    <figure><img src="../../../../.gitbook/assets/image (467).png" alt=""><figcaption></figcaption></figure>
*   **wait\_for\_update**\
    Enabling this optional feature will send a signal to Google's tags to [wait for an update](https://developers.google.com/tag-platform/security/guides/consent?hl=en#tracking\_consent\_state). \
    Enter a value in milliseconds to control the waiting time before the data is sent.\
    This can be useful if you are experiencing timing issues. Otherwise, you can leave it blank!\


    <div align="center">

    <figure><img src="../../../../.gitbook/assets/image (468).png" alt=""><figcaption></figcaption></figure>

    </div>
*   **ads\_data\_redaction**\
    set [ads\_data\_redaction](https://developers.google.com/tag-platform/security/guides/consent?hl=en#redact\_ads\_data) to ON to further redact your advertising data when "ad\_storage" is "denied"

    <figure><img src="../../../../.gitbook/assets/image (471).png" alt=""><figcaption></figcaption></figure>
*   **url\_passthrough**\
    [URL passthrough](https://developers.google.com/tag-platform/security/guides/consent?hl=en#passthroughs) option can be used to send event and session-based analytics (including conversions) without cookies across pages.\
    \


    <figure><img src="../../../../.gitbook/assets/image (470).png" alt=""><figcaption></figcaption></figure>

### 3-Activate the feature on your privacy banner(s)

`Sources > Privacy Banners > Select your banner(s)`\
Go at the edition step of your privacy banner, open the settings menu to turn ON Google Consent Mode Signal\


<figure><img src="../../../../.gitbook/assets/image (489).png" alt=""><figcaption></figcaption></figure>

The privacy setup is done! You can now Generate and Deploy your Privacy Banner.\
_\*At this point, Consent Mode will not affect the behaviour of your tags. Please follow the next steps!_

<figure><img src="../../../../.gitbook/assets/image (474).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The activation of this option will automatically add an Google Policy URL, it's a legal requirement for using Google Consent Mode on your website. Feel free to adapt your introduction text if needed
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (473).png" alt=""><figcaption></figcaption></figure>

### 4- Advanced Mode: Remove your privacy constraints from Google tags

To setup the version "Advanced" of the Consent Mode, remove Commanders Act Privacy rules from all the Google tags, now it's managed by Google Consent Mode\
`Data Governance > Consent Management > Categories` see tab `assign tags`\
\- **Remove the privacy constraints from Google tags**\
**- Save**

<figure><img src="../../../../.gitbook/assets/image (476).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
For Basic Consent Mode, skip the step 4! \
Keep your Privacy rules applied on your tags
{% endhint %}

### 5-Generate your container(s)

Go on `Sources > WebContainers > generation step`\
\
For a single container setup, generate your container with privacy banner(s) included

For a multiple container setup, generate all your containers. The privacy banner(s) should be linked to the first loaded container to ensure that the Consent Mode signal is always sent correctly.

{% hint style="warning" %}
_If you was using the Consent Mode v1 tag, don't forget to delete or deactivate it! It's useless now._
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (477).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**What about the triggers ?**

The consent mode is compatible with the **container loaded** trigger. If your Google tags are already set to this, it will work without any trigger modification

But we also provide a custom trigger, if needed!\
When a Consent Mode signal is sent, our product pushes **tC.event.consent\_signal\_ready**\
You can use it to trigger your tags.

If your site is an SPA, you can keep your **tC.event.page/pageview**... as trigger for  your Google tags. The same goes for your click/scroll tags.
{% endhint %}

### 6-Tests & deployment

#### Deployment

We recommend to test you setup on a UAT environment if possible.

<figure><img src="../../../../.gitbook/assets/image (478).png" alt="" width="377"><figcaption></figcaption></figure>

#### Test your configuration

There's 3 different ways to verify your Consent Mode setup:

{% tabs %}
{% tab title="Test with plugin Google Tag Assistant" %}
The easiest way to verify your setup is using the [Tag Assistant](https://tagassistant.google.com/) plugin provided by Google.\
\
**The "Consent" event should always be sent before any hits from the tags**\
The status "**On-page Default**" should be the same then the ones you setup at the [step 2](consent-mode-in-commanders-act-tms.md#categories)

<figure><img src="../../../../.gitbook/assets/image (479).png" alt=""><figcaption></figcaption></figure>

**After Consent**, the "**On-page Update**" status should correspond to the consent given on the privacy banner

<figure><img src="../../../../.gitbook/assets/image (480).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Test with the browser's console" %}
Feel as a developer? You can also look into the console to verify the Google arguments pushed in dataLayer Google.\
Type `dataLayer` then press `Enter`



<figure><img src="../../../../.gitbook/assets/image (482).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Test with a payload verification" %}
One last method to verify your setup is possible: check into the payload of your hits in the network.\
The consent status is fed by the "gcd" parameter

<figure><img src="../../../../.gitbook/assets/image (483).png" alt=""><figcaption></figcaption></figure>

#### Possibles values for gcd parameter

`gcd` is included in all hits to Google services, even if Consent Mode isn’t active.

It encodes values for four consent signals (`ad_storage`, `analytics_storage`, `ad_user_data`, and `ad_personalization`), and it includes information how the consent signal was generated.

The format of the string is this:

`&gcd=11<ad_storage>1<analytics_storage>1<ad_user_data>1<ad_personalization>5`

The string starts with `11`, uses `1` to separate the different consent signals, and ends with a number like `5` (or sometimes something else) to mark the end.



<table><thead><tr><th width="97">Letter</th><th>Description</th><th width="142">Example value</th><th>Meaning</th></tr></thead><tbody><tr><td><code>l</code></td><td>The lowercase L means that the signal has not been set with Consent Mode</td><td><code>11l1p1l1l5</code></td><td>only analytics_storage has been denied by default</td></tr><tr><td><code>p</code></td><td>denied by default <br>(no update)</td><td><code>11p1p1p1p5</code></td><td>all consent states are denied by default</td></tr><tr><td><code>q</code></td><td>denied both by default and after update</td><td><code>11p1q1p1p5</code></td><td>the user updated their consent choice to set analytics_storage to denied after it was already set to denied by default</td></tr><tr><td><code>t</code></td><td>granted by default <br>(no update)</td><td><code>11t1t1t1t5</code></td><td>all consent states are granted by default</td></tr><tr><td><code>r</code></td><td>denied by default and granted after update.</td><td><code>11r1r1r1r5</code></td><td>the user grants consent to all services after they were first denied by default</td></tr><tr><td><code>m</code></td><td>denied after update <br>(no default)</td><td><code>11p1m1p1p5</code></td><td>all other states were denied by default, but analytics_storage was only set after the user denied it</td></tr><tr><td><code>n</code></td><td>granted after update <br>(no default)</td><td><code>11n1n1n1n5</code></td><td>the site did not set a default consent state and instead set all states to granted after the user chose so</td></tr><tr><td><code>u</code></td><td>granted by default and denied after update.</td><td><code>11u1u1u1u5</code></td><td>the user withdrew all consents after they were set to granted by default</td></tr><tr><td><code>v</code></td><td>granted both by default and after update.</td><td><code>11v1v1v1v5</code></td><td>all states were granted by default and by user confirmation</td></tr></tbody></table>
{% endtab %}
{% endtabs %}



## Migration guide

**For customers who has already implemented  the Consent Mode v1**: \
You can activate the built in feature as described above (don't forget to deactivate your actual consent mode tag)\
However, if you really want to keep your actual setup and simply update your tag, then you can refer to this documentation!

Summarizing all recommended steps:

1. Access your [Commanders Act account](https://app.commandersact.com/).
2. Update your tag template.
3. Test and deploy your container(s).

### Update your tag template

Go on page `"Sources" > "Web containers"`\
Select you "Google Consent Mode with Trust" tag.

<figure><img src="../../../../.gitbook/assets/image (455).png" alt=""><figcaption></figcaption></figure>

**Update the js code block** of your tag with the following code, then **save** to obtain the new fields

<details>

<summary>code snippet to update</summary>

```
<script language="javascript">
window.dataLayer = window.dataLayer || [];
var gtag = function (){
	dataLayer.push(arguments);
};
tC.internalvars.getRegion = function(a){
	a = a.toString().replace(/\s/g, '');
	a = a.split(",");
	return a;
};
tC.internalvars.setRegion = function(a) {
	tC.internalvars.regionArray = tC.internalvars.getRegion(a);
	if (((typeof tC.privacy.isEnable !== "undefined") && tC.privacy.isEnable()) && (tC.internalvars.regionArray.length > 0) && (tC.internalvars.regionArray[0] !== "") && (typeof tC.internalvars.consentSettings !== "undefined")) {
		tC.internalvars.consentSettings.region = tC.internalvars.regionArray;
		return true;
	} else return false;
};
tC.internalvars.setWait = function(a){
	if (((typeof tC.privacy.isEnable !== "undefined") && tC.privacy.isEnable()) && (isNaN(parseInt(a, 10)) === false) && (parseInt(a, 10) > 0) && (typeof tC.internalvars.consentSettings !== "undefined")) {
    	tC.internalvars.consentSettings.wait_for_update = parseInt(a, 10);
      	return true;
    } else return false;
};
tC.internalvars.setConsentCommand = function(a, b, c){
	tC.internalvars.isRegionSet = tC.internalvars.setRegion(b);
	tC.internalvars.isDelaySet = tC.internalvars.setWait(c);
  	if (((typeof tC.privacy.isEnable !== "undefined") && tC.privacy.isEnable()) && (tC.internalvars.isRegionSet || tC.internalvars.isDelaySet)){
    	return "default";
    }
  	if ((a.toString() === "default") || (a.toString() === "update")){
		return a;
	}
	if ((typeof tC.privacy.isEnable !== "undefined") && tC.privacy.isEnable()) return "default";
	else return "update";
	return "default";
};
gtag('set', 'developer_id.dOWVhY2', true);
tC.internalvars.consentSettings = {
	'ad_storage': (#DEFAULT_AD_CATEGORY# !== "")?#DEFAULT_AD_CATEGORY#:"denied",
	'analytics_storage': (#DEFAULT_ANALYTICS_CATEGORY# !== "")?#DEFAULT_ANALYTICS_CATEGORY#:"denied",
	'functionality_storage': (#DEFAULT_FUCTIONALITY_CATEGORY# !== "")?#DEFAULT_FUCTIONALITY_CATEGORY#:"denied",
	'personalization_storage': (#DEFAULT_PERSONALIZATION_CATEGORY# !== "")?#DEFAULT_PERSONALIZATION_CATEGORY#:"denied",
	'security_storage': (#DEFAULT_SECURITY_CATEGORY# !== "")?#DEFAULT_SECURITY_CATEGORY#:"denied",
  'ad_personalization':(#DEFAULT_AD_PERSONALIZATION_CATEGORY# !== "")?#DEFAULT_AD_PERSONALIZATION_CATEGORY#:"denied",
  'ad_user_data':(#DEFAULT_AD_USER_DATA_CATEGORY# !== "")?#DEFAULT_AD_USER_DATA_CATEGORY#:"denied" 
}
console.log(tC.internalvars.consentSettings);
console.log("REGION: " + #REGION#);
console.log("WAIT_FOR_UPDATE: " + #WAIT_FOR_UPDATE#);
// Default command on page load
console.log("INFO: default command");
gtag('consent', tC.internalvars.setConsentCommand("default", #REGION#, #WAIT_FOR_UPDATE#), tC.internalvars.consentSettings);
tC.internalvars.ga_url_passthrough = #URL_PASSTHROUGH#;
tC.internalvars.ga_ads_data_redaction = #ADS_DATA_REDACTION#;
if ((typeof tC.internalvars.consentSettings !== "undefined") && (tC.internalvars.consentSettings.ad_storage === "denied")) {
	if ((tC.internalvars.ga_url_passthrough !== "") && ((tC.internalvars.ga_url_passthrough.toLowerCase() === "true") || (tC.internalvars.ga_url_passthrough.toLowerCase() === "false"))) {
		gtag('set', 'url_passthrough', (tC.internalvars.ga_url_passthrough.toLowerCase() === "true"));
	}
	if ((tC.internalvars.ga_ads_data_redaction !== "") && ((tC.internalvars.ga_ads_data_redaction.toLowerCase() === "true") || (tC.internalvars.ga_ads_data_redaction.toLowerCase() === "false"))) {
		gtag('set', 'ads_data_redaction', (tC.internalvars.ga_ads_data_redaction.toLowerCase() === "true"));
	}
}
tC.internalvars.setConsentUpdateCommand = function(result){
	tC.internalvars.consentSettings = {
	    'ad_storage': (result.consent.categories[#TRUST_AD_CATEGORY_ID#].status === "on") ? "granted" : "denied",
	    'analytics_storage': (result.consent.categories[#TRUST_ANALYTICS_CATEGORY_ID#].status === "on") ? "granted" : "denied",
	    'functionality_storage': (result.consent.categories[#TRUST_FUNCTIONALITY_CATEGORY_ID#].status === "on") ? "granted" : "denied",
	    'personalization_storage': (result.consent.categories[#TRUST_PERSONALIZATION_CATEGORY_ID#].status === "on") ? "granted" : "denied",
	    'security_storage': (result.consent.categories[#TRUST_SECURITY_CATEGORY_ID#].status === "on") ? "granted" : "denied",
	  'ad_personalization':(result.consent.categories[#TRUST_AD_PERSONALIZATION_CATEGORY_ID#].status === "on") ? "granted" : "denied",
  'ad_user_data':(result.consent.categories[#TRUST_AD_USER_DATA_CATEGORY_ID#].status === "on") ? "granted" : "denied"
    }
	console.log(tC.internalvars.consentSettings);
	console.log("REGION: " + #REGION#);
	console.log("WAIT_FOR_UPDATE: " + #WAIT_FOR_UPDATE#);
	// Update command on page load
	console.log("INFO: update command");
	gtag('consent', tC.internalvars.setConsentCommand("update", #REGION#, #WAIT_FOR_UPDATE#), tC.internalvars.consentSettings);
};
cact('consent.get', function (result) {
	if (result.consent.status !== "unset") {
      tC.internalvars.setConsentUpdateCommand(result);
	}
});
// Triggered on consent changes
cact('consent.onUpdate', function (result) {
  	tC.internalvars.setConsentUpdateCommand(result);
});
</script>
```

</details>

<figure><img src="../../../../.gitbook/assets/image (456).png" alt=""><figcaption></figcaption></figure>

You can **do your mapping** on the new fields & **Save** again your tag

Set the by default status of the \*new categories (denied or granted)

<figure><img src="../../../../.gitbook/assets/image (459).png" alt=""><figcaption></figcaption></figure>

Enter the ID of your privacy categories to link them with the Google's \*new categories\
If needed, you can find your privacy ID on the page `Data Governance > Consent Management > Categories`

<figure><img src="../../../../.gitbook/assets/image (460).png" alt=""><figcaption></figcaption></figure>

Don't forget to save your settings

<figure><img src="../../../../.gitbook/assets/image (461).png" alt=""><figcaption></figcaption></figure>



### Generate & Deploy your container



<figure><img src="../../../../.gitbook/assets/image (462).png" alt="" width="563"><figcaption></figcaption></figure>



### Update your Privacy Banner(s)

Go on page `Source > Privacy Banners > edition step`

{% hint style="danger" %}
**LEGAL REQUIREMENT**

Add the following link to the Google Consent Mode Policy in your Privacy Center or in your Vendors menu&#x20;

[https://policies.google.com/privacy](https://policies.google.com/privacy)

Don't forget to generate & deploy your privacy banner(s) once you've made this additional setting.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (463).png" alt=""><figcaption></figcaption></figure>

You can now Generate & Deploy your privacy banner(s)

<figure><img src="../../../../.gitbook/assets/image (464).png" alt=""><figcaption></figcaption></figure>

**You are up to date**, you can test your settings on your website. \
Don't hesitate to refer at the [test step above](consent-mode-in-commanders-act-tms.md#id-6-tests-and-deployment) to get tips & tricks.
