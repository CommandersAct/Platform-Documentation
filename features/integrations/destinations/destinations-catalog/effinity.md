# Effinity

Send purchase or lead events to Effinity.

## How to configure Effinity

Information needed:

### Advertiser ID

Must be replaced by the applicable Effinity advertiser ID. Consult your account contact or assigned integrator if in any doubt.&#x20;

### Conversion type Sale / Lead

&#x20;The "Conversion Type" bound with your activity - This can be either "Sale" or "Lead". \
\- If conversion type = lead ⇾ only `generate_lead` event is supported\
\- If conversion type = sale ⇾ only `purchase` event is supported

### Effinity Cookie Name

Enter a cookie name holding Effinity key tracking values.&#x20;

{% hint style="info" %}
Expected cookie structure: \
"\[ID\_COMPTEUR],\[PROD\_ID],\[EFFI\_ID],\[EFFI\_ID2]" (E.g."01010101,1234,567890,098765")
{% endhint %}
