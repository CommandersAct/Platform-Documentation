# A record

The A record is the recommended solution for tracking purposes using 1st party cookies.

## What is a `A record?`

A record (A for Address) is a DNS record type. It is a match between a domain and an IP address. It points the hostname to the IP address.

cs.example.com ⇒ IP Address : 36.283.49.384

## How the A record creation process works

Since there is a link between the domain and the IP address, we need to have control over it. Otherwise, it would be very complicated for maintenance: we will have to ask customers to change their configuration each time we want to upgrade the platform.

We therefore ask customers to delegate part of their DNS to us. This means that we will be able to configure the corresponding IP address for the delegated domain.

The process is quite simple, on Administration / Domain Management interface, click on 'Add subdomain' to add a domain name that will be delegated.\
Select A record and select how to provide the certificate:

* Use Let's Encrypt certificate: with this method, the certificate will be automatically generated. Follow the steps on the interface, no action is required on your side.
*   Use your own certificate: this will require to provide the following elements:

    \- The SSL certificate(s) linked to the subdomain(s) entered above\
    \- The key of the certificate\
    \- The chain of the certificate\
    If you need assistance, please contact the Commanders Act support team.

![](<../../../.gitbook/assets/Capture d’écran 2022-05-20 à 14.50.37 (1).png>)

## A record setup with Let's encrypt

Customers' DNS should be configured with A record information (ask your IT department).

Screenshot

Click on "Validate configuration" and this will test the DNS configuration.

## A record setup with your own certificate

Customers' DNS should be configured with A record information (ask your IT department).

Screenshot

Click on "Validate configuration" and this will test the DNS configuration.
