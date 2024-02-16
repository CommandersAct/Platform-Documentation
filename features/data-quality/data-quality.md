# Sources data quality

On the _Health_ menu, you will find _Sources data quality_. It shows all events received per sources.

<figure><img src="../../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

You can visualize the evolution of number of events received (purchase, add to cart...) in the last 24 hours.

Below, you can analyze in detail each event and have more details about errors and rejection:

<figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

**FAILED** the event is in error status, can be caused by an error 404, a timeout, etc...

**FILTERED** the event has been filtered (based on the conditions created in Normalized Datalayer.)

**INVALID ACCEPTED** means the property has been removed, but it is not blocking for the event, this one has been received without the concerned property. You should fix the property to receive it.

**INVALID REJECTED** means one or many properties are missing or don't have good values. As a result, the full event was rejected, you should fix it to receive the event.

**VALID** the event has been collected correctly, this means your sources are sending the data expected in your specifications.



You can also visualize the data quality for a specific source, when you click on a source, you have a dedicated tab '_Data Quality_' available with same info but filtered for the source you selected:

<figure><img src="../../.gitbook/assets/image (442).png" alt=""><figcaption></figcaption></figure>
