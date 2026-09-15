# Destination Logs Exporter

{% hint style="info" %}
This destination is subject to additional charges.
{% endhint %}

You can easily export your destination's raw logs using the **Destination Logs Exporter**.\
This destination will allow you to export to an SFTP all outgoing requests issued by the destinations you choose, and to analyze in these logs all the details, including the originating events that led to the outgoing requests.

### Configuration

#### **Data Source**

Select one or more destinations from which you'd like to export your data.

<figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-3aa6519ed3113c5948bf051cad735f597682264c%2Fimage.png?alt=media" alt=""><figcaption></figcaption></figure>

### Settings

1. **Name your destination** and pick the environment you'd like to work in.
2.  **Select a storage connector**. This can be set up in **Administration > Connector Credentials**.\
    Only FTP, Amazon S3 & Google Cloud Storage are currently supported\\

    <figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-db74f73ef90aaa0e90b7e31a32dd89abea068971%2Fimage.png?alt=media" alt="" width="375"><figcaption></figcaption></figure>
3.  **Specify the file name and extension** (default is CSV).\
    \\

    <figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-436e78ddcb041b16e29c3cebc425aad821529014%2Fimage.png?alt=media" alt=""><figcaption></figcaption></figure>
4.  By default, your export file will not be compressed. If needed, **you can compress your file to GZIP format**.\
    \\

    <figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-771be649880597c124228eae3e20d378e61a4a98%2Fimage.png?alt=media" alt=""><figcaption></figcaption></figure>
5.  **Set the data separator**, like commas for CSV files (e.g., value1,value2).\
    \\

    <figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-add178a9a763b2bc1680e79cb8cd5c4c9863e68a%2Fimage.png?alt=media" alt=""><figcaption></figcaption></figure>

### Activation

* Enable your destination to start exporting!
* **Modify the timezone** if necessary.
* Adjust the **export frequency and time window** to suit your needs.

<figure><img src="https://1259070148-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-Mk6XpTQ2LaRLcr2tA-d%2Fuploads%2Fgit-blob-6ad410672977f4169fc65922492bdfd1a4c3907e%2Fimage.png?alt=media" alt=""><figcaption></figcaption></figure>
