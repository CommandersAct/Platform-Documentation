# Hosting

### Hosting types

We offer two ways for your container's hosting:

* Via our **CDN** (Content Delivery Network): provides you a total autonomous deployment. Our CDN is having a 99.9% of SLA
* Via your site’s **web servers**, managed by your IT department or outside technical provider. With this hosting option, you can choose a **synchronization method** (automatic or manual) for transmitting the modifications made for your site in the Commanders Act interface.\
  \
  In all cases : for a new workspace, you will be must to configure the connector on the platform. Use the menu Administration => Connector Credentials to add a new connector

<figure><img src="../../../../../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

### FTP connector configuration

Simply fill in all fields of the form:\
**Name:** Give an explicit name to your connector\
**Containers:** Select any client-side containers you want to associate with the connector\
**Protocol:** Select the type of File Transfer Protocol you need. We recommend to using SFTP, for security reasons\
**Host:** Enter the main domain or IP address of your FTP repository\
**Port:** Enter your standard port ID (SFTP is 22, FTP is 21, FTPS is 21...)\
**Path:** Enter the path of your repository. Should end with a "/" (see below example)\
**User:** Login to access of your FTP\
**Password/Key:** if there's a password or a key associated to your FTP, enter this information here&#x20;

<figure><img src="../../../../../../.gitbook/assets/image (4) (2).png" alt="" width="563"><figcaption></figcaption></figure>

### CDN connector configuration

It's almost identical to the FTP connector, there is only 2 more steps:\
Select a CDN vendor (EdgeCast or Akamai) \
Setup the "Purge" part (use the Account ID, Token and Purge URL provided by your CDN vendor)

<figure><img src="../../../../../../.gitbook/assets/image (9).png" alt="" width="509"><figcaption></figcaption></figure>

### URL connector configuration

Just give an explicit name, enter the correct URL and select any client-side container(s) you want to associate with the connector

<figure><img src="../../../../../../.gitbook/assets/image (14).png" alt="" width="539"><figcaption></figcaption></figure>

### Amazon S3 connector configuration

It's almost identical to the FTP connector. However, it requires a bucket as the host:

<figure><img src="../../../../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

### Google Cloud Storage connector configuration

fill in all fields of the form:\
**Name:** Give an explicit name to your connector\
**Bucket:** Enter the main domain or IP address of your FTP repository\
**Path:** Enter the path of your repository. Should end with a "/" (see below example)\
**Project ID:** Enter the id of the project in Google Cloud Storage. Can be found in Google Cloud JSON Key file\
**Private key ID:** Enter your private RSA Key Id for Google Cloud Services. Can be found in Google Cloud JSON Key file\
**Private key:** Enter the password associated to your Private Key ID. Still can be found in Google Cloud JSON Key file\
**Google Account Email:** Enter the client Google Cloud Services email used for authentication. You can find it in Google Cloud JSON Key file\
**Client Id:** Enter the client Google Cloud Services Id. Still can be found in Google Cloud JSON Key file\
**Client X509 Cert URL:** Enter the client custom X509 URL for Google Cloud Services. Can be found in Google Cloud JSON Key file\


<figure><img src="../../../../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The Private Key field must include the comments 'BEGIN PRIVATE KEY' and 'END PRIVATE KEY'\
\
All the characters "`\n"` present in the Private Key must be replaced by "enter" (jump line)
{% endhint %}

```
//example for the private key:

-----BEGIN PRIVATE KEY-----
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxp
yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy0
zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzA
aaaaaaaaaaaaaaaaaaaaaaa=
-----END PRIVATE KEY-----
```



### Bing Ads connector configuration

Simply follow the step by step guide provided by Bing:

<figure><img src="../../../../../../.gitbook/assets/image (13).png" alt="" width="311"><figcaption></figcaption></figure>

### Facebook Ads connector configuration

Simply follow the step by step guide provided by Facebook:

<figure><img src="../../../../../../.gitbook/assets/image (15) (2).png" alt="" width="392"><figcaption></figcaption></figure>

### Criteo connector configuration

Simply follow the step by step guide provided by Criteo:

<figure><img src="../../../../../../.gitbook/assets/image (5) (4).png" alt="" width="326"><figcaption></figcaption></figure>

### Google Ads connector configuration

Simply follow the step by step guide provided by Google Ads:

<figure><img src="../../../../../../.gitbook/assets/image (11).png" alt="" width="407"><figcaption></figcaption></figure>

###

{% hint style="info" %}
Please note! Deletion of this connector credential is final. By removing access to a login, you will no longer be able to use it for this or any other site. This means you'll have to create a new one if you need it in the future.&#x20;

If destinations from other sites use this identifier, they too will no longer work.

In case this login is currently used by at least one destination, our interface will display a list of the concerned destination(s) (only for the current site, it may affect some destinations on other sites)&#x20;
{% endhint %}

### Snapchat connector configuration

Simply follow the step by step guide provided by Snapchat:

<figure><img src="../../../../../../.gitbook/assets/image (6) (1) (1).png" alt="" width="343"><figcaption></figcaption></figure>

### Adobe Analytics connector configuration

Simply follow the step by step guide provided by Adobe:\
For more information, please refer to the [dedicated page](../../../../../destinations/destinations-catalog/adobe/adobe-analytics.md)

<figure><img src="../../../../../../.gitbook/assets/image (12).png" alt="" width="415"><figcaption></figcaption></figure>

### Equativ connector configuration

Simply follow the step by step guide provided by Equativ:

<figure><img src="../../../../../../.gitbook/assets/image (3) (2).png" alt="" width="340"><figcaption></figcaption></figure>

### Test & Debug

Once your connector configuration is done, you can click on the Test button to check that it's working properly. \
If it is correct, then you will see the following message:

<figure><img src="../../../../../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>



{% hint style="warning" %}
Common errors:\


* your directory is not writable
* mistake on host/port/path
* Insufficient space
* Network outage = server/ or network problem
{% endhint %}

