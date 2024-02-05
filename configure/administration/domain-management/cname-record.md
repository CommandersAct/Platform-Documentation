# CNAME record

In the customer's DNS, the use of a CNAME pointing to a Commanders Act server allows to set cookie as a first party.

You need to combine CNAME with the [CAID on-premise cookie](cookie-caid.md) to get the most out of it.

## What is a CNAME?

A CNAME, or Canonical Name, is an entry within the Domain Name System (DNS) that specifies where someone can find your web pages. You'll use the CNAME to associate your custom domain with our products.

Running a domain name is a multi-sided process thanks to the many DNS management possibilities offered by web hosting providers. Most of the hosts today offer multiple options for control over your domain's DNS settings, among them being the CNAME Records.

## How the CNAME creation process works

The customer should create a subdomain and setup CNAME entries to point to our server (and create as many subdomains as existing domains).\
Example:

[client.com](http://client1.com/) creates a subdomain [XYZ.client.com](http://pheonix.client1.com/) pointing to Commanders Act server.\
From now on, our tags will now call [XYZ.client.com](http://pheonix.client1.com/) instead of our 3rd party domain (commander1) and response will set a cookie on main domain .[client.com](http://client1.com/) which is allowed by main web browsers.

Then please indicate the subdomain on our platform: Admin / Domain Management.

![](<../../../.gitbook/assets/Capture d’écran 2022-05-19 à 15.16.09.png>)

The customer must decide if the SSL encryption on the new subdomain they created is done with ‘Let’s Encrypt’ or with their own certificate. In the former case, nothing to do; in the later case, follow the instruction on the domain management page.

Moreover, change on every tag the URL to specify the 1st party domain.



## Activate the domain

Click on "Containers Integration", this will allow the domain to be included in the container configuration.

<figure><img src="../../../.gitbook/assets/image (438).png" alt=""><figcaption></figcaption></figure>

All Commanders Act tags will switch to first party collection.

This action will affect Consent, Deduplication, Campaign, Segment, Server Side

{% hint style="warning" %}
At this point, **WebContainers and Privacy banners** should be **regenerated and deployed.**
{% endhint %}

## What happens when I have 2 or more domains?

It prioritizes the domain of the website where the container is loaded. If no domain matches the domain of the website, the 1st in the list is used.
