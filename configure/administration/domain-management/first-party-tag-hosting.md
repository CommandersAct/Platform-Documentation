# First-Party Tag Hosting

Our first-party tag hosting feature ensures that ad blockers do not interrupt responsible data tracking unfairly. This is in line with privacy best practice and GDPR compliance.

By configuring your first-party tag hosting, you can change the host of your external files used in your tags (from Web Containers).

Looking for an alternative way to avoid the effects of ad blockers and maintain tracking? You've come to the right place!

### Domain Configuration <a href="#configuration" id="configuration"></a>

{% hint style="info" %}
**Prerequisite:** have a valid CNAME in your DNS configuration 2 CNAMEs are required: 1 for file's hosting & 1 for SSL certification More info [here](https://doc.commandersact.com/configure/administration/domain-management/cname-record#how-the-cname-creation-process-works)
{% endhint %}

#### Add your domain <a href="#add-your-domain" id="add-your-domain"></a>

{% hint style="info" %}
If you have already configured a "domain" in "domain management" for [CDN first-party hosting](cdn-1st.md), you can skip the first step
{% endhint %}

If you haven't declared any domains yet, you will see the following message on the 'First-Party Tag Hosting' page:

<figure><img src="../../../.gitbook/assets/image (593).png" alt=""><figcaption></figcaption></figure>

#### Declare your sub-domain

Go on Administration > Domain Management

Look to the menu Domain Management for CDN 1st party

Click on "Add Subdomain"

<figure><img src="https://doc.commandersact.com/~gitbook/image?url=https%3A%2F%2F1259070148-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Mk6XpTQ2LaRLcr2tA-d%252Fuploads%252FJOzHcxaubfZ1xj8e4rPm%252Fimage.png%3Falt%3Dmedia%26token%3D4399df89-c793-4b03-879c-316dd7e4e71d&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=eb335c41&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Enter your subdomain name

<figure><img src="https://doc.commandersact.com/~gitbook/image?url=https%3A%2F%2F1259070148-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Mk6XpTQ2LaRLcr2tA-d%252Fuploads%252Fwfdd2qAGn8DO4zrWKf6Z%252Fimage.png%3Falt%3Dmedia%26token%3D7c9b882d-8c19-4ad9-a34d-d88aab983e86&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=685022c5&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Once saved, the new subdomain will be displayed in your list

<figure><img src="https://doc.commandersact.com/~gitbook/image?url=https%3A%2F%2F1259070148-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Mk6XpTQ2LaRLcr2tA-d%252Fuploads%252FjFvZazapjb70p3P7C65K%252FCapture%2520d%27%25C3%25A9cran%25202024-10-10%2520174605.png%3Falt%3Dmedia%26token%3Dfbc2f0bd-ff7d-475c-ac0e-4e0a36a5f2e8&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=eb43facf&#x26;sv=2" alt=""><figcaption></figcaption></figure>

#### Validate your configuration <a href="#validate-your-configuration" id="validate-your-configuration"></a>

Once your subdomain is added, you need to validate your configuration, to obtain a Valid Certificate It will be validated only if your CNAME has been [properly configured](https://doc.commandersact.com/configure/administration/domain-management/cname-record#how-the-cname-creation-process-works)

<figure><img src="https://doc.commandersact.com/~gitbook/image?url=https%3A%2F%2F1259070148-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Mk6XpTQ2LaRLcr2tA-d%252Fuploads%252F5uiiwW2s90Q7GXwlyYRs%252Fimage.png%3Falt%3Dmedia%26token%3Dad5e875d-e363-4d37-aedb-6798ec7c19ee&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=2e3c08ec&#x26;sv=2" alt=""><figcaption></figcaption></figure>

#### Activation <a href="#activation" id="activation"></a>

As long as the domain isn't activated, your workspace will not be impacted by your configuration. Once activated, all your Web Container(s) & Privacy banner(s) will be hosted on the new subdomain(s)

<figure><img src="https://doc.commandersact.com/~gitbook/image?url=https%3A%2F%2F1259070148-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-Mk6XpTQ2LaRLcr2tA-d%252Fuploads%252FgkwACrxitTUuEr47QeQQ%252Fimage.png%3Falt%3Dmedia%26token%3Dc2f5cc32-5660-4f9c-bd5d-f5fd2fa534b7&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=1ec4a9bf&#x26;sv=2" alt=""><figcaption></figcaption></figure>

### JS URL File declaration <a href="#activation" id="activation"></a>

Go to 'Administration > First-Party Tag Hosting' to declare the JavaScript (JS) external files/libraries that you want to host with the First-Party feature.

Click on "add js url" button

<figure><img src="../../../.gitbook/assets/image (594).png" alt=""><figcaption></figcaption></figure>

Then, all you need to do is declare your JavaScript file URL

<figure><img src="../../../.gitbook/assets/image (595).png" alt=""><figcaption></figcaption></figure>

Make sure the 'Enable hosting' toggle button is set to 'ON'.

<figure><img src="../../../.gitbook/assets/image (596).png" alt=""><figcaption></figcaption></figure>

Our product will automatically suggest you a safe renaming of your file, but you can change it if you wish. This will be mentioned in the path of the hosting url \
(example: "https://my\_sub\_name.domain.com/<mark style="background-color:yellow;">8461026763.js</mark>"

If you change the name, be careful to use a name that will not be blocked by ad blockers.\
(eg. don't use the partner name, such as "gtag")

<figure><img src="../../../.gitbook/assets/image (597).png" alt=""><figcaption></figcaption></figure>

You can Save! The configuration is complete and your new JS URL has been added to your list.

<figure><img src="../../../.gitbook/assets/image (598).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Note: If you have configured multiple subdomains, the file will be available on each of them.
{% endhint %}

example:

<figure><img src="../../../.gitbook/assets/image (602).png" alt=""><figcaption></figcaption></figure>

### Update the URL of your file(s) call(s)

Last step before complete setup!

Replace the related JavaScript file URL called inside your tag's code of your Web Containers.

<figure><img src="../../../.gitbook/assets/image (599).png" alt=""><figcaption></figcaption></figure>

Then you can regenerate and deploy your Web Container(s)

### How to test

Go on your website, check in the network of the browser console.

Your new first-party hosting URL file will replace the partner one

<figure><img src="../../../.gitbook/assets/image (600).png" alt=""><figcaption></figcaption></figure>

The partner JavaScript file URL will no longer appears

<figure><img src="../../../.gitbook/assets/image (601).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Please note: Please note that there is a 'refresh' delay applicable to this feature. It may take up to one hour to upload your file to the First-Party configuration.\
Our development team is currently working to reduce this time.
{% endhint %}
