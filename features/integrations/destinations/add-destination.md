# Destinations overview

## What is a destination ?

## Destination list

Find here the full list of destinations already configured.

You can search a destination by name and filter on environment (production or staging), status (active or inactive) or on specific source.

![](<../../../.gitbook/assets/Destination overview.png>)

4 sections are available: Cloud mode, Device mode, Audience and Raw Data.

### Cloud mode

It refers to event based destinations that execute on the server (aka server-side tags): destinations that run in real-time and push your events (purchases, page views...).

### Device mode (soon)

It refers to destinations that needs to be executed in the browser (aka client-side tags). For example : survey tag, A/B testing, heatmapping tool, live chat, web notification, ...\
Currently, client-side tags are manageable in the web containers section. They will move progressively on the device mode section.

### Audience

It refers to destinations that push user's segments, each time a user enter or leave a segment you created.

### Raw Data

It refers to scheduled destinations, through file exchange like FTP, S3 or Cloud Storage.

## Trend and Health

The trend represents the evolution of number of events pushed to the destination on the last month (maximum data retention period).

Health allow to quickly visualize the status of the destination, if everything is well sent (sunny) or not (stormy) on the last hour.\
Click on it to access to Event Delivery interface and have more details (see also [Event Delivery documentation](event-delivery.md)).

![](<../../../.gitbook/assets/Capture d’écran 2022-03-01 à 15.13.05.png>)
