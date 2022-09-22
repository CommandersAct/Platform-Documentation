# Facebook Offline conversion

Send your offline conversions (like purchases made in stores) directly to Facebook.

Create a new stream, select Facebook Offline conversion connector and enter the information needed:

![](<../../../../.gitbook/assets/image (28).png>)

## How to find the Offline Event Set Id?

On Facebook Business Manager, [https://business.facebook.com/](https://business.facebook.com/) click on Events Manager and create a new data source:

![](<../../../../.gitbook/assets/image (22).png>)

Then select offline:

![](<../../../../.gitbook/assets/image (36).png>)

Finish the data source configuration and retrieve the Event set ID:

![](<../../../../.gitbook/assets/image (11).png>)

## How to generate the token?

Still on Facebook Business Manager, [https://business.facebook.com/](https://business.facebook.com/) click on Business settings and select system user:

![](<../../../../.gitbook/assets/image (5).png>)

Create a system user (if you don't already have one) and generate a token:

![](<../../../../.gitbook/assets/image (19).png>)

Select ads\_management authorization:

![](<../../../../.gitbook/assets/image (7).png>)

Copy and paste the token on our connector configuration page.
