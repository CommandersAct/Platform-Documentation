# Destination Logs Exporter (closed beta)

You can easily export your destination's raw logs using the **Destination Logs Exporter**. \
This destination will allow you to export to an SFTP all outgoing requests issued by the destinations you choose, and to analyze in these logs all the details, including the originating events that led to the outgoing requests.

### Configuration

#### **Data Source**

Select one or more destinations from which you'd like to export your data.

<figure><img src="../../../.gitbook/assets/image (3) (4).png" alt=""><figcaption></figcaption></figure>



### Settings

1. **Name your destination** and pick the environment you'd like to work in.
2.  **Select a storage connector**. This can be set up in **Administration > Connector Credentials**.\
    Only FTP, Amazon S3 & Google Cloud Storage are currently supported\


    <figure><img src="../../../.gitbook/assets/image (4) (7).png" alt="" width="375"><figcaption></figcaption></figure>
3.  **Specify the file name and extension** (default is CSV).\
    \


    <figure><img src="../../../.gitbook/assets/image (6) (6).png" alt=""><figcaption></figcaption></figure>
4.  By default, your export file will not be compressed. If needed, **you can compress your file to GZIP format**.\
    \


    <figure><img src="../../../.gitbook/assets/image (7) (6).png" alt=""><figcaption></figcaption></figure>
5.  **Set the data separator**, like commas for CSV files (e.g., value1,value2).\
    \


    <figure><img src="../../../.gitbook/assets/image (8) (6).png" alt=""><figcaption></figcaption></figure>

### Activation

* Enable your destination to start exporting!
* **Modify the timezone** if necessary.
* Adjust the **export frequency and time window** to suit your needs.

<figure><img src="../../../.gitbook/assets/image (2) (7).png" alt=""><figcaption></figcaption></figure>
