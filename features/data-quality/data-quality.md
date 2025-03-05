# Sources data quality

On the _Health_ menu, you will find _Sources data quality_.

You can visualize the evolution of your event data quality over time, filter by sources or environment (default to Production)

<figure><img src="../../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

You can setup an alert to know in realtime if some of your event violate your [validation rules](event-specification.md).

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

You can analyze in detail each event and have more details about errors, and a shortcut to [fix the error in the Data Cleansing feature](data-cleansing/).

<figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

**FAILED** the event is in error status, can be caused by an error 404, a timeout, etc...

**FILTERED** the event has been filtered (based on the conditions created in Normalized Datalayer.)

**INVALID ACCEPTED** means the property has been removed, but it is not blocking for the event, this one has been received without the concerned property. You should fix the property to receive it.

**INVALID REJECTED** means one or many properties are missing or don't have good values. As a result, the full event was rejected, you should fix it to receive the event.

**VALID** the event has been collected correctly, this means your sources are sending the data expected in your specifications.



You can also visualize the data quality for a specific source, when you click on a source, you have a dedicated tab '_Data Quality_'tap  available with same info but filtered for the source you selected:

<figure><img src="../../.gitbook/assets/image (442).png" alt=""><figcaption></figcaption></figure>

The quality score of events is represented by a weather icon:&#x20;

* <img src="../../.gitbook/assets/image (17) (1) (1).png" alt="" data-size="line">sunny if the percent of correct events is equal to 100%
* <img src="../../.gitbook/assets/image (15) (2) (1).png" alt="" data-size="line">cloudy between 95% and 99.99%
* <img src="../../.gitbook/assets/image (16) (1).png" alt="" data-size="line">rainy between 90 and 95%
* <img src="../../.gitbook/assets/image (14) (2) (1).png" alt="" data-size="line">stormy below 90%
