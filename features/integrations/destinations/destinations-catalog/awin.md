# Awin

Send purchase or lead events to Awin.

## How to configure Awin

Information needed:

### Advertiser ID

Must be replaced by the applicable Awin advertiser program ID. Consult your account contact or assigned integrator if in any doubt.&#x20;

### Conversion type Sale / Lead

&#x20;The "Conversion Type" bound with your activity - This can be either "Sale" or "Lead". \
\- If conversion type = lead ⇾ only `generate_lead` event is supported\
\- If conversion type = sale ⇾ only `purchase` event is supported

### Commission group code

The code for the commission group you want to attribute the transaction to. \
If no commission group is specified, this should be set to DEFAULT.&#x20;

{% hint style="info" %}
Accepted characters for the commissionGroup code are alphanumerics (letter in upper case), underscore '\_' , point '.' and minus '-'
{% endhint %}
