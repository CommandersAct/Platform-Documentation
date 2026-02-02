# Amazon Consent Signal

### How to use the Amazon Consent Mode feature ? <a href="#how-to-use-the-google-consent-mode-feature" id="how-to-use-the-google-consent-mode-feature"></a>

{% hint style="info" %}
Before getting started: **Amazon Consent requires activation of geolocation API**. Ask your consultant or to our support team to get an activation token for your Site ID
{% endhint %}

#### 1- Activate the feature on your workspace <a href="#id-1-activate-the-feature-on-your-workspace" id="id-1-activate-the-feature-on-your-workspace"></a>

Login on[ your workspace](https://app.commandersact.com/) Go on page `Data Governance > Consent Management > Settings` Turn **On** the option Amazon Consent Mode. The sub-menu "Amazon Consent Mode settings" will appear

<figure><img src="../../../../.gitbook/assets/image (208).png" alt=""><figcaption></figcaption></figure>

#### 2-Configure your settings <a href="#id-2-configure-your-settings" id="id-2-configure-your-settings"></a>

**Categories**

Select your appropriate Privacy category from the drop-down list for each Amazon's category.

<figure><img src="../../../../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>



#### 3-Regenerate and deploy your CMP banner(s)

You're ready to regenerate your privacy banner(s) and deploy them in production

<figure><img src="../../../../.gitbook/assets/image (218).png" alt=""><figcaption></figcaption></figure>

Once it's deployed, our CMP will send the Consent Signal as expected by Amazon.

In your Web Container, you can remove your privacy rules of your Amazon client side tags, the Amazon Consent Signal replace the privacy rules.
