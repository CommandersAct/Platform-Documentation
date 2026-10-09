# Event delivery

The Event Delivery interface allows you to see if data is reaching your destination and if the platform found any problems sending your source data.

![](https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-955d48d931d303f955e9397fc14a73d73bb40746%2FEvent%20Delivery%20full.png?alt=media)

Delivery statistics are stored during 1 month (no statistics after 1 month).

You can select on the calendar a shortcut period (last hour) or a specific period (from 12/11 to 15/11 for example).

The UI is divided into three sections that provide information on the platform's capacity to provide your source data: Key Metrics, Delivery Trends and Error Details.

### 1. Key Metrics <a href="#id-2-key-metrics" id="id-2-key-metrics"></a>

![](https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-ef15371280dfcbc94bb7aeeb1589e4197bbb02be%2FCapture%20d%E2%80%99e%CC%81cran%202022-03-01%20a%CC%80%2015.16.59.png?alt=media)

* **Delivered:** This displays the number of messages successfully delivered to a destination within the time period you choose.\
  The % of events delivered is represented by a weather icon:
  * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-163dc1c992023f53c20d113409bb912186250023%2Fimage.png?alt=media" alt="" data-size="line">sunny if the % of events successfully delivered is above 95%
  * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-94c962956761a0054ef182741477830d95612ef1%2Fimage.png?alt=media" alt="" data-size="line">cloudy between 90 and 95%
  * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-324a3eddd3902d82ae9256fe27edce87de88227d%2Fimage.png?alt=media" alt="" data-size="line">rainy between 50 and 90%
  * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-2c5911845dcaef4ab1aa809eec35c0d0f1a62ed2%2Fimage.png?alt=media" alt="" data-size="line">stormy below 50%
*   **Not Delivered:** This number represents the number of messages that the platform was unable to deliver. If this number is more than zero, the causes for this failure are listed in the errors' table below.

    The % of events not delivered is represented by a weather icon:

    * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-163dc1c992023f53c20d113409bb912186250023%2Fimage.png?alt=media" alt="" data-size="line">sunny if the % of failures is below 5%
    * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-94c962956761a0054ef182741477830d95612ef1%2Fimage.png?alt=media" alt="" data-size="line">cloudy if the % of failures is below 10%
    * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-324a3eddd3902d82ae9256fe27edce87de88227d%2Fimage.png?alt=media" alt="" data-size="line">rainy if the % of failures is between 10% and 50%
    * <img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-2c5911845dcaef4ab1aa809eec35c0d0f1a62ed2%2Fimage.png?alt=media" alt="" data-size="line">stormy if the % of failures is above 50%

The % of difference display the comparison with the same previous period: ex if I select 2 days, it will display the difference with the previous 2 days, if I select 1 week it will display the difference with the previous week.

The small trend graph represents the global evolution of delivered and not delivered events on the maximum delivery data retention period, which is 1 month.

* **Filtered events**: it corresponds to events that are not sent, because of a filter.
  * Filter related to consents: corresponds to the User Consent Category entered the filter section
  * Filter related to conditions: corresponds to the filter defined in the filter section

<figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-c980f61758e248da66274d52ed4b38c0dd6cd772%2FCapture%20d%E2%80%99e%CC%81cran%202023-05-30%20a%CC%80%2011.55.01.png?alt=media" alt=""><figcaption></figcaption></figure>

### 2. Delivery trends <a href="#id-3-error-details" id="id-3-error-details"></a>

Visualize directly the evolution of delivered and not delivered events on a larger period. You can change the period you want to visualize: last hour, last day, last week or last month.

![](https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-da9e85645ed58b9310f54abb4b76989d6dc55f63%2FCapture%20d%E2%80%99e%CC%81cran%202022-03-01%20a%CC%80%2015.17.19.png?alt=media)

### 3. Error details <a href="#id-3-error-details" id="id-3-error-details"></a>

The table's objective is to offer you with an overview of the various errors we've observed in a particular time period, as well as the most significant information about them. The table's rows are all clickable and expand to provide more information.

You can debug immediately errors encountered thanks to the description of the error and the way to solve it.

![](https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-ca87f44adf5368c656c7b00e9eb0912f2060a1c7%2FCapture%20d%E2%80%99e%CC%81cran%202022-03-01%20a%CC%80%2015.16.27.png?alt=media)

## Automatic retries

Commanders Act automatically retries failed deliveries to server-side destinations when a timeout, network error, temporary destination error (5xx), or rate limit (429) occurs.

The success card distinguishes events delivered immediately from those delivered after a retry. The "After retry" counter shows the total number of events successfully delivered after a retry during the selected period, rather than the number of retry attempts.

## Alerting

You can subscribe to alerts, to receive notifications if the delivered ratio fall below the threshold you have chosen (e.g. if you have less than 90% of your events delivered, you can set an alert and be alerted).\
You will be alerted as soon as the event occurs, and you can define a reminder, to be alerted as long as the problem remains : every hour, every day, every week.

![](https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-59ad6ca41fdf9dbc1d27f2fcfb59f69feb078a01%2Fimage.png?alt=media)

Currently, three channels are available to receive alerts : email, Slack and Microsoft Teams. In a near future platform notifications and a webhook will also be available.

## Delivery API

All the data of this UI is available in real-time through delivery API, see our Config API for the complete documentation.
