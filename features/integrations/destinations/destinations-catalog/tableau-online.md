# Tableau Online

For this connector, the concept is to send to Tableau each X minutes new events in **append** mode (ex : pageviews, clicks, impressions, ...)

![](https://tagcommander.atlassian.net/wiki/download/attachments/993198085/image2019-7-2\_9-55-56.png?version=1\&modificationDate=1562054156962\&cacheVersion=1\&api=v2)

We are able to push Data to Tableau every 10 minutes (full export or delta).

\
Append mode will add new lines to existing table in Tableau, so the stream has to be configured to **differential** (export only new events), like this :

![](https://tagcommander.atlassian.net/wiki/download/attachments/993198085/image2019-7-2\_9-53-52.png?version=1\&modificationDate=1562054032676\&cacheVersion=1\&api=v2)

\
For **users** universe, it's different, you can't choose "append" because users are updated continously and you don't want to add each times the same users, so you have to choose **overwrite** mode for this univers, with an export each night (because it will take hours to send all users to Tableau) (edited)

\
Tableau online doesn't support updates\
It offers only append or overwrite

![](https://tagcommander.atlassian.net/wiki/download/attachments/993198085/image2019-7-2\_9-53-3.png?version=1\&modificationDate=1562053984899\&cacheVersion=1\&api=v2)

### Help to fill the connectors input :  <a href="#howtoexportdatatotableauonline-helptofilltheconnectorsinput" id="howtoexportdatatotableauonline-helptofilltheconnectorsinput"></a>

\
**Url Server**\
The URL for the Tableau server on which the data is published.\
For Tableau Online, specify [https://online.tableau.com](https://online.tableau.com/).\
\--\
**Site name**\
The site id is independent of the site name, and it is indicated in the URL when you view the site in a browser. For example, if the URL for the page you see after signing in to Tableau Online is\
[https://online.tableau.com/t/vernazza/views](https://online.tableau.com/t/vernazza/views)\
the site id is vernazza.\
\--\
**date source name**\
The name of the data source, as published to Tableau Online.\
\--\
**username**\
Valid Tableau Online user.\
\--\
**password**\
The password for the specified Tableau Online user.
