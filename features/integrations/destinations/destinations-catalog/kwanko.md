# Kwanko

Send purchase or lead events to Kwanko.

## How to configure Kwanko

Information needed:

### Tracking ID

Your "Tracking Id" as provided by Kwanko. It's used to identify your campaigns.

### Conversion type Sale / Lead

&#x20;The "Conversion Type" bound with your activity - This can be either "Sale" or "Lead". \
\- If conversion type = lead ⇾ only `generate_lead` event is supported\
\- If conversion type = sale ⇾ only `purchase` event is supported

### Cookie Click Id

For each click on Kwanko links, a new "Click Id" is automatically generated. This can be found as value for the parameter "`kwks2s`" in landings. Input the cookie name holding this value.
