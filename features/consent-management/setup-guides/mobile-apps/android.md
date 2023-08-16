# Android

Having the user consent is essential to send sensible information like the IDFA/AAID. To prevent having to manually save the consent asked to the user and manually using it with our SDKs, we created a module helping you do it automatically.This module will gather the consent and will:

* Display a consent page (if needed)
* Save consent and reload it every time the application is launched.
* Save and check the validity of the consent. The validity duration is set to 13 months.
* Send a hit to our servers to record the consent.
* Enable or disable the SDK. (if used alongside the SDK)
* Add the categories automatically to the hits the SDK sends. (if used alongside the SDK)

{% hint style="success" %}
Privacy's Implementation Guide:\
[https://github.com/CommandersAct/AndroidV5/tree/master/TCConsent](https://github.com/CommandersAct/AndroidV5/tree/master/TCConsent)
{% endhint %}

