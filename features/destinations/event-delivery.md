# Event delivery

The Event Delivery interface allows you to see if data is reaching your destination and if the platform found any problems sending your source data.

![](<../../.gitbook/assets/Event Delivery full.png>)

Delivery statistics are stored during 1 month (no statistics after 1 month).

You can select on the calendar a shortcut period (last hour) or a specific period (from 12/11 to 15/11 for example).

The UI is divided into three sections that provide information on the platform's capacity to provide your source data: Key Metrics, Delivery Trends and Error Details.

### 1. Key Metrics <a href="#2-key-metrics" id="2-key-metrics"></a>

![](<../../.gitbook/assets/Capture d’écran 2022-03-01 à 15.16.59.png>)

* **Delivered:** This displays the number of messages successfully delivered to a destination within the time period you choose.\
  The % of events delivered is represented by a weather icon:
  * <img src="../../.gitbook/assets/image (17) (2).png" alt="" data-size="line">sunny if the % of events successfully delivered is above 95%
  * <img src="../../.gitbook/assets/image (15) (2) (1).png" alt="" data-size="line">cloudy between 90 and 95%
  * <img src="../../.gitbook/assets/image (16) (1).png" alt="" data-size="line">rainy between 50 and 90%
  * <img src="../../.gitbook/assets/image (14) (2) (1).png" alt="" data-size="line">stormy below 50%
*   **Not Delivered:** This number represents the number of messages that the platform was unable to deliver. If this number is more than zero, the causes for this failure are listed in the errors' table below.

    The % of events not delivered is represented by a weather icon:

    * <img src="../../.gitbook/assets/image (17) (2).png" alt="" data-size="line">sunny if the % of failures is below 5%
    * <img src="../../.gitbook/assets/image (15) (2) (1).png" alt="" data-size="line">cloudy if the % of failures is below 10%
    * <img src="../../.gitbook/assets/image (16) (1).png" alt="" data-size="line">rainy if the % of failures is between 10% and 50%
    * <img src="../../.gitbook/assets/image (14) (2) (1).png" alt="" data-size="line">stormy if the % of failures is above 50%

The % of difference display the comparison with the same previous period: ex if I select 2 days, it will display the difference with the previous 2 days, if I select 1 week it will display the difference with the previous week.

The small trend graph represents the global evolution of delivered and not delivered events on the maximum delivery data retention period, which is 1 month.

* **Filtered events**: it corresponds to events that are not sent, because of a filter.
  * Filter related to consents: corresponds to the User Consent Category entered the filter section
  * Filter related to conditions: corresponds to the filter defined in the filter section

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-05-23 à 11.40.50 (1).png" alt=""><figcaption></figcaption></figure>

### 2. Delivery trends <a href="#3-error-details" id="3-error-details"></a>

Visualize directly the evolution of delivered and not delivered events on a larger period. You can change the period you want to visualize: last hour, last day, last week or last month.

![](<../../.gitbook/assets/Capture d’écran 2022-03-01 à 15.17.19.png>)

### 3. Error details <a href="#3-error-details" id="3-error-details"></a>

The table's objective is to offer you with an overview of the various errors we've observed in a particular time period, as well as the most significant information about them. The table's rows are all clickable and expand to provide more information.

You can debug immediately errors encountered thanks to the description of the error and the way to solve it.

![](<../../.gitbook/assets/Capture d’écran 2022-03-01 à 15.16.27.png>)

## Alerting

You can subscribe to alerts, to receive notifications if the delivered ratio fall below the threshold you have chosen (e.g. if you have less than 90% of your events delivered, you can set an alert and be alerted).\
You will be alerted as soon as the event occurs, and you can define a reminder, to be alerted as long as the problem remains : every hour, every day, every week.

![](<../../.gitbook/assets/image (3) (1) (2).png>)

Currently, three channels are available to receive alerts : email, Slack and Microsoft Teams. In a near future platform notifications and a webhook will also be available.

## Delivery API

All the data of this UI is available in real-time through delivery API, see our [Config API](../../developers/config-api.md) for the complete documentation.
