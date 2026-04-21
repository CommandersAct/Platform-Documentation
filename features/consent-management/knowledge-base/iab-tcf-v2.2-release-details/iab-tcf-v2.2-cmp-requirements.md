# IAB TCF v2.3 CMP requirements

{% hint style="info" %}
The IAB TCF v2.3 CMP banner has the same requirements then 2.2. If your banner was already compliant to these standards, then you don't need to change anything on your banner
{% endhint %}

## 1st Layer

The standard text has evolved with more precise list of usage of datas, and the total number of IAB TCF vendors must be displayed

<figure><img src="../../../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If your banner has a custom text, you can use this function to display the number of vendors on the first layer\
`tC.privacy.getNbIabVendors()`
{% endhint %}

{% hint style="warning" %}
IAB TCF requirements are very strict. If you wish to display a custom text, we strongly recommend you to ask a validation from IAB team. You can also refer to this[ cmp UX UI requirements guide](https://iabeurope.eu/all-news/im-a-cmp-am-i-doing-it-right-2-cmp-ui-ux-requirements-part-3/)
{% endhint %}

## 2nd Layer (purposes menu)

### Buttons Accept All/Refuse All are required

If you don't have yet an accept all / refuse all buttons in your privacy center, you must add them manually. You can refer to the step n°2 of [this page](iab-tcf-v2.2-migration-guide-web.md) for setup help

<figure><img src="../../../../.gitbook/assets/image (147).png" alt=""><figcaption></figcaption></figure>

### The automatic text of Purposes has evolved

<figure><img src="../../../../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

### There's no more "Legal Description" it is replaced by "Examples"

<figure><img src="../../../../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

### **New TC string special purpose**

The TCF will add a new (special) purpose to the classification of purposes in the TCF, informing their users that they are capturing and sharing data subject choices via the TC String.\
The name of this new special purpose is _"Use limited data to select content"_ (ID 11)

### Legitimate interest buttons will be removed on the following Purposes:

* purpose 3 (create a personalized ads profile)
* purpose 4 (select personalized ads)
* purpose 5 (create a personalized content profile)
* purpose 6 (select a personalized content profile)

## 3rd Layer (Vendors Menu)

3 major changes for the information provided by the Vendors

* They can provide a cookie policy url in multiple languages (the displayed url will be the same then the browser language)
* They must show the data retention period for each purpose
* They must show data they will collect
