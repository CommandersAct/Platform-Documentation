# Sources data quality

On the _Health_ menu, you will find _Sources data quality_. It shows all events received per sources.

![](<../../.gitbook/assets/Capture d’écran 2022-06-29 à 11.35.40.png>)

You can visualize the evolution of number of events received (purchase, add to cart...) in the last 24 hours.

Below, you can analyze in detail each event and have more details about errors and rejection:

![](<../../.gitbook/assets/Capture d’écran 2022-06-29 à 11.36.57.png>)

**INVALID ACCEPTED** means the property has been removed, but it is not blocking for the event, this one has been received without the concerned property. You should fix the property to receive it.

**INVALID REJECTED** means one or many properties are missing or don't have good values. As a result, the full event was rejected, you should fix it to receive the event.



You can also visualize the data quality for a specific source, when you click on a source, you have a dedicated tab '_Data Quality_' available with same info but filtered for the source you selected:

![](<../../.gitbook/assets/Capture d’écran 2022-06-29 à 11.39.38.png>)
