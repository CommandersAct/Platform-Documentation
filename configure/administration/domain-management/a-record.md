# A record

The A record is another solution to set cookies as first party.

## What is a `A record?`

A record (A for Address) is a DNS record type. It is a match between the domain and IP address. It points the hostname to the IP address.

cs.example.com ⇒ IP Address : 36.283.49.384

## How the A record creation process works

Since there is a link between the domain and the IP address, we need to have control over it. Otherwise, it would be very complicated for maintenance: we will have to ask customers to change their configuration each time we want to upgrade the platform.

We therefore ask customers to delegate part of their DNS to us. This means that we will be able to configure the corresponding IP address for the delegated domain.

The process is quite simple, on Administration / Domain Management interface, click on 'Add subdomain' to add a domain name that will be delegated. \
Select A record and select the certificate:

* Use Let's Encrypt certificate: follow the steps on the interface, and you have nothing else to do
* Use your own certificate: you also have this possibility.

Then test the configuration, and we take care of everything.

![](<../../../.gitbook/assets/Capture d’écran 2022-05-20 à 14.50.37 (1).png>)
