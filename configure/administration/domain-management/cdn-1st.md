# CDN 1st

Our CDN 1st feature helps ensure that ad blockers do not unfairly interrupt responsible data tracking. This is in line with privacy best practice and GDPR compliance. \
\
By configuring your CDN 1st, you'll be able to change the host of your Web Container(s) & Privacy banner(s). \
\
Are you looking for an additional approach to avoid the effects of ad blockers and keep tracking? You've come to the right place!

## Configuration

{% hint style="info" %}
**Prerequisite:** have a valid CNAME in your DNS configuration\
2 CNAMEs are required: 1 for file's hosting & 1 for SSL certification\
More info [here](cname-record.md#how-the-cname-creation-process-works)
{% endhint %}

### Add your domain

Go on Administration > Domain Management

Look to the menu Domain Management for CDN 1st

Click on "Add Subdomain"

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Enter your subdomain name

<figure><img src="../../../.gitbook/assets/image (9).png" alt="" width="460"><figcaption></figcaption></figure>

Once saved, the new subdomain will be displayed in your list

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2024-10-10 174605.png" alt=""><figcaption></figcaption></figure>

### Validate your configuration

Once your subdomain is added, you need to validate your configuration, to obtain a Valid Certificate\
It will be validated only if your CNAME has been [properly configured](cname-record.md#how-the-cname-creation-process-works)

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

### Activation

As long as the domain isn't activated, your workspace will not be impacted by your configuration.\
Once activated, all your Web Container(s) & Privacy banner(s) will be hosted on the new subdomain(s)

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### Multiple Domains Management

Your configuration is using multiple work spaces?\
CDN 1st allows you to share a subdomain between different sites IDs, as long as they belong to the same "invoicing account".

{% hint style="info" %}
**Pre requisite:** must have **validated and activated** subdomains on other work spaces
{% endhint %}

Instead of "Add subdomain", click on "Load subdomain"

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Select in the drop down's menu the subdomain you need to use on your workspace.

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2024-10-09 184809.png" alt=""><figcaption></figcaption></figure>

A loaded domain is activated by default. If you want to stop it on your workspace, simply click the button "stop using this subdomain". The subdomain will remains activated on the site where it is configured.

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Good to know! \
On site copy, the CDN 1st configuration(s) will not be copied, you'll need to load subdomains from the "parent" site.
{% endhint %}

### Go live with CDN 1st

When your setup is done, the Deploy step of Web Containers & Privacy banners are now impacted.\
That means your files will now hosted on your new domain.

To ensure stability, re generate & re deploy all your Web Container(s), and Privacy banner(s)

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Web Container's deployment: example for 1 subdomain configured</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Web Container's deployment: example for multiple subdomains configured</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Privacy's deployment: example for 1 subdomain configured</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Privacy's deployment: example for multiple subdomain configured</p></figcaption></figure>

:rocket:   Congratulations! Your configuration is done!
