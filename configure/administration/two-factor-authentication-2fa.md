# Two-factor authentication (2FA)

The 2FA authentication, for two-factor authentication, is a way to reinforce the security to access to the platform.

The goal is to provide a way to login on the platform and then receive an email with a unique token. By doing this, we have a double authentication with first the login/password and then the code received by email, it is a double security.

It has to be activated on the profile level (profile management), using the switch button on each profile you want to activate the option.



<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Switch button activation on profile management page</p></figcaption></figure>

Once this option is activated, the platform will request an access token sent by email.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

\
This token will be active for 30 days (on the same browser and IP), that means it will request a new one as soon as the token expire (or if you change your browser or IP).

On the login page, there is an option to login without the double authentication, if you do this you will be able to connect only to sites on which 2FA is not activated on your profile.

{% hint style="warning" %}
**What happen if I don’t receive the token sent?**

You can retry to login, click on the dedicated button to retry. Please check also your spam folder. After the 2 attempts, if you still received nothing, please contact our customer support immediately.
{% endhint %}
