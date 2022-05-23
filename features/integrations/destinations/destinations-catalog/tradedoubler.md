# Tradedoubler



Send purchase or lead events to Tradedoubler.

## How to configure Tradedoubler

Information needed:

### Organization ID

Your organization identifier as provided by Tradedoubler.

### Conversion type Sale / Lead

&#x20;The "Conversion Type" bound with your activity - This can be either "Sale" or "Lead". \
\- If conversion type = lead ⇾ only `generate_lead` event is supported\
\- If conversion type = sale ⇾ only `purchase` event is supported

### Event ID

The event identifier for the lead/sale taking place and as provided by Tradedoubbler.

### Cookie name (tduid)

Tradedoubler's unique tracking identifier that is set in a cookie and session variable by the redirect page.

### Checksum

This is part of Tradedoubler's fraud protection measures, and we highly recommend you implement it. Your Tradedoubler contact will explain how it should be implemented.

### User ID type:

* User email
* User ID
