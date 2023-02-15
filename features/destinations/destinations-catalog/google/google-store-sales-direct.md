# Google Store Sales Direct

[Google ](https://about.google/)is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software.\
The connector Google Store Sales Direct allows you to send conversions to Google Ads.

> Store sales measurement allows you to use your sales data in a privacy-safe way to understand how much value your ads are truly driving for in-store purchases. By uploading and matching transaction data from your business, you can see how your ads translate into offline purchases.

More [information](https://support.google.com/google-ads/topic/9941533?hl=en\&ref\_topic=7280668)

## How it works? <a href="#how-it-works" id="how-it-works"></a>

From your Data Commander account, you can send your conversions through our connector. [https://support.google.com/google-ads/answer/10018944?hl=en\&ref\_topic=9941533#zippy=%2Cbenefits-of-uploading-store-sales-data-in-google-ads](https://support.google.com/google-ads/answer/10018944?hl=en\&ref\_topic=9941533#zippy=%2Cbenefits-of-uploading-store-sales-data-in-google-ads)​

We send conversions to your FTP, and then you have to push these conversions from the FTP to Google Ads: [https://support.google.com/google-ads/answer/10018944?hl=en\&ref\_topic=9941533#zippy=%2Cbenefits-of-uploading-store-sales-data-in-google-ads%2Cschedule-an-upload](https://support.google.com/google-ads/answer/10018944?hl=en\&ref\_topic=9941533#zippy=%2Cbenefits-of-uploading-store-sales-data-in-google-ads%2Cschedule-an-upload)​

1. DataCommander ⇒ Customer FTP (Connector Google Store Sales Direct)
2. Customer FTP ⇒ Google Ads (you should configure the file exchange between your FTP and your Google Ads account like described on the documentation above)

## How to configure it? <a href="#how-to-configure-it" id="how-to-configure-it"></a>

On the connector setup interface, select all users or select a segment you want to use.

![](https://2406699966-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-Me4KyQWoYQhMjxapjIB%2F-Me4Mako0T6E6i4cQ-zK%2FCapture%20d%E2%80%99e%CC%81cran%202021-07-08%20a%CC%80%2011.06.09.png?alt=media\&token=403092d6-d617-40b0-8d55-52dbb492c651)

For example, you can send only conversions that belong to specific users that you selected in your segment (users living in Germany only, for example).

You should select all the variables requested by Google: Conversion Time, Conversion Value, Conversion Currency, and at least one Email variable.

Full list and format [here](https://support.google.com/google-ads/answer/10018336?hl=en\&ref\_topic=9941533).

All personal data (email, first name, phone number...) are hashed in SHA-256.

There are also 3 variables specific to that connector:

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2021-01-29 à 10.19.21.png" alt=""><figcaption></figcaption></figure>

Loyalty Rate:

> * The percent of overall sales in your data file that you can associate with a customer
> * The Loyalty Rate needs to be between “0” and “1” (excluding “0”)
>
> For example:
>
> * 0.5
> * 0.2
> * 0.8

Transaction Upload Rate:

> * The ratio of sales you’re uploading to the overall sales that you can associate with a customer
> * While the Transaction Upload Rate can be between “0” and “1,” we recommend uploading all customer associated sales and setting the Transaction Upload Rate to “1”.
>
> For example:
>
> * 0.5
> * 0.2
> * 0.8

Conversion name:

> * The name of the conversion action that you’d like to import
> * Must match the same spelling and capitalization of the conversion action in your Google Ads account
>
> For example:
>
> * SS\_customer\_signups
> * SS\_customer\_purchases

More [details](https://support.google.com/google-ads/answer/10018336?hl=en\&ref\_topic=9941533)
