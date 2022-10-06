# Facebook Offline conversion

Send your offline conversions (like purchases made in stores) directly to Facebook.

Create a new stream, select Facebook Offline conversion connector and enter the information needed:

![](<../../../../.gitbook/assets/image (8) (1) (1).png>)

## How to find the Offline Event Set Id?

On Facebook Business Manager, [https://business.facebook.com/](https://business.facebook.com/) click on Events Manager and create a new data source:

![](<../../../../.gitbook/assets/image (6) (1) (1) (1).png>)

Then select offline:

![](<../../../../.gitbook/assets/image (7) (1) (1) (1) (1).png>)

Finish the data source configuration and retrieve the Event set ID:

![](<../../../../.gitbook/assets/image (5) (1) (1) (1).png>)

## How to generate the token?

Still on Facebook Business Manager, [https://business.facebook.com/](https://business.facebook.com/) click on Business settings and select system user:

![](<../../../../.gitbook/assets/image (2) (1) (1) (1) (1).png>)

Create a system user (if you don't already have one) and generate a token:

![](<../../../../.gitbook/assets/image (3) (1).png>)

Select ads\_management authorization:

![](<../../../../.gitbook/assets/image (4) (1) (1).png>)

Copy and paste the token on our connector configuration page.
