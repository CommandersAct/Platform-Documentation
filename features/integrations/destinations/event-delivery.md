# Event delivery

The Event Delivery interface allows you to see if data is reaching your destination and if the platform found any problems sending your source data.

Delivery statistics are stored during 1 month (no statistics after 1 month).

You can select on the calendar a shortcut period (last hour) or a specific period (from 12/11 to 15/11 for example).

The UI is divided into three sections that provide information on the platform's capacity to provide your source data: Key Metrics, Delivery Trends and Error Details.&#x20;

### 1. Key Metrics <a href="2-key-metrics" id="2-key-metrics"></a>

* **Delivered:** This displays the number of messages successfully delivered to a destination within the time period you choose.
* **Not Delivered:** This number represents the number of messages that the platform was unable to deliver. If this number is more than zero, the causes for this failure are listed in the errors' table below.

The % of difference display the comparison with the same previous period: ex if I select 2 days, it will display the difference with the previous 2 days, if I select 1 week it will display the difference with the previous week.

The small trend graph represents the global evolution of delivered and not delivered events on the maximum delivery data retention period, which is 1 month.

### 2. Delivery trends <a href="3-error-details" id="3-error-details"></a>

Visualize directly the evolution of delivered and not delivered events on a larger period. You can change the period you want to visualize: last hour, last day, last week or last month.

### 3. Error details <a href="3-error-details" id="3-error-details"></a>

The table's objective is to offer you with an overview of the various errors we've observed in a particular time period, as well as the most significant information about them. The table's rows are all clickable and expand to provide more information.

You can debug immediately errors encountered thanks to the description of the error and the way to solve it.

## Alerting

You can subscribe to alerts, to receive notifications if the delivered ratio fall below the threshold you have chosen (e.g. if you have less than 60% of your events delivered, you can set an alert and be alerted). You will be alerted as soon as the event occurs and you can define a reminder: every hour, every day, every week. Of course,

You can receive an email alert and, later, we will add more channels like platform notification or webhook to configure your own alerts on your tools like Slack.

## Delivery API

All the data of this UI is available in real-time through delivery API, see our [Config API](../../../developers/config-api.md) for the complete documentation.