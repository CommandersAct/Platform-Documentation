# Event delivery

The Event Delivery interface allows you to see if data is reaching your destination and if the platform found any problems sending your source data.

The UI is divided into three sections that provide information on the platform's capacity to provide your source data: Key Metrics, Error Details, and Delivery Trends.

### 1. Key Metrics <a href="2-key-metrics" id="2-key-metrics"></a>

* **Delivered:** This displays the number of messages successfully delivered to a destination within the time period you choose.
* **Not Delivered:** This number represents the number of messages that the platform was unable to deliver. If this number is more than zero, the causes for this failure are listed in the errors table below.

### 2. Error details <a href="3-error-details" id="3-error-details"></a>

The table's objective is to offer you with an overview of the various errors we've observed in a particular time period, as well as the most significant information about them. The table's rows are all clickable and expand to provide more information.

## Alerting

You can subscribe to alerts, to receive notifications if the delivered ration fall bellow the threshold you have choosen.&#x20;

## Delivery API

All the data of this UI is available in realtime through delivery api, see our [Config API](../../../developers/config-api.md) for the complete documentation.
