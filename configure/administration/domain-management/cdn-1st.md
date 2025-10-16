# First party hosting

Our 1st party hosting feature helps ensure that ad blockers do not unfairly interrupt responsible data tracking. This is in line with privacy best practice and GDPR compliance. \
\
By configuring your CDN 1st party hosting, you'll be able to change the host of your Web Container(s) & Privacy banner(s). \
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

Look to the menu Domain Management for CDN 1st party

Click on "Add Subdomain"

<figure><img src="../../../.gitbook/assets/image (613).png" alt=""><figcaption></figcaption></figure>

Enter your subdomain name

<figure><img src="../../../.gitbook/assets/image (9) (7).png" alt="" width="460"><figcaption></figcaption></figure>

Once saved, the new subdomain will be displayed in your list

<figure><img src="../../../.gitbook/assets/image (614).png" alt=""><figcaption></figcaption></figure>

### Validate your configuration

Once your subdomain is added, you need to validate your configuration, to obtain a Valid Certificate\
It will be validated only if your CNAME has been [properly configured](cname-record.md#how-the-cname-creation-process-works)

<figure><img src="../../../.gitbook/assets/image (615).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (616).png" alt=""><figcaption></figcaption></figure>

Once you configuration has been validated, Web Containers & Privacy files will be hosted on our regular CDN URL and on you First Party domain URL. For more details, look to the "[Go Live with 1st Party Hosting](cdn-1st.md#go-live-with-1st-party-hosting)" section of this documentation

### Multiple work spaces Management

Your configuration is using multiple work spaces?\
1st party hosting allows you to share a subdomain between different sites IDs, as long as they belong to the same "invoicing account".

{% hint style="info" %}
**Pre requisite:** must have **validated and activated** subdomains on other work spaces
{% endhint %}

Instead of "Add subdomain", click on "Load subdomain"

<figure><img src="../../../.gitbook/assets/image (617).png" alt=""><figcaption></figcaption></figure>

Select in the drop down's menu the subdomain you need to use on your workspace.

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2024-10-09 184809.png" alt=""><figcaption></figcaption></figure>

A loaded domain is activated by default. If you want to stop it on your workspace, simply click the button "stop using this subdomain". \
Note: The subdomain will remains activated on the site where it is configured.

<figure><img src="../../../.gitbook/assets/image (618).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Good to know! \
On site copy, the CDN 1st configuration(s) will not be copied, you'll need to load subdomains from the "parent" site.
{% endhint %}

### Go live with 1st party Hosting

When your setup is done, the Deploy step of Web Containers & Privacy banners are now impacted.\
That means your files will now hosted on your new domain.

To ensure stability, re generate & re deploy all your Web Container(s), and Privacy banner(s)

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Web Container's deployment: example for 1 subdomain configured</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Web Container's deployment: example for multiple subdomains configured</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Privacy's deployment: example for 1 subdomain configured</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Privacy's deployment: example for multiple subdomain configured</p></figcaption></figure>

:rocket:   Congratulations! Your configuration is done!

{% hint style="info" %}
Good to know: When your CDN First Party is configured, you will need to replace the URLs of your web container(s) on your website. The "regular" CDN URL will remain active, but to enjoy the benefits of first party hosting, you will need to use the CDN 1st party URLs.
{% endhint %}

### Multiple domains management

Do you have many different hosting domains? (e.g. domain.fr, domain.it, domain.eu ...) \
We recommend that you create 1 Cname for each domain to avoid the effects of ad blockers as much as possible.

If, for technical reasons, you can only create 1 Cname common to all your site domains, you must use a custom js snippet code to manage the situation.

In the custom javascript block of your web container, insert the following line of code

`tC.privacy.defaultCdnDomain = "enter_here_your_cdn_first(cname)_url"`

