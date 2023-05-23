# Creation and modification

To create/add a container, go to the “**Web Containers**” tab on the platform and click “**ADD CONTAINER**”:

<figure><img src="../../../../../../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

A configuration window will appear with 3 main tabs:

* “[**General**](creation-and-modification.md#general)“: to manage basic container options, such as naming your container
* “[**Synchronization**](creation-and-modification.md#synchronization)“: to manage container updating options
* “[**Advanced**](creation-and-modification.md#advanced)“: to manage advanced container options&#x20;

After configuring the various container options, click “Add”

### **General**

<figure><img src="../../../../../../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

Simply fill the “**Name**“ field with Container’s wanted name



### **Synchronization**

<figure><img src="../../../../../../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

Mode: Synchronization modes for the container:

* **FTP/CDN**: This mode hosts the container on an FTP or CDN server (the server must be previously configured in Administration => Connector Credentials). By clicking this option, the “**Set as deployed and send to FTP**” synchronization mode will be proposed in the “**DEPLOY**” step.
* **Amazon S3**: This mode hosts the container on an FTP or CDN server (the server must be previously configured in Administration => Connector Credentials). By clicking this option, the “**Set as deployed and send to AWS**” synchronization mode will be proposed in the “**DEPLOY**” step.
* **Update by batch from permanent link**: this mode activates a permanent link to the last container version deployed. This mode can be useful when manually updating the container on your site or if you use a batch that regularly restores the last container version on the site. By clicking this option, the “**Set as deployed and use external URL**” synchronization mode will be proposed in the “**DEPLOY**” step.
* **Custom URL**: this mode calls a URL when deploying the container (the URL must be previously configured in Administration => Connector Credentials).  This URL refers to a script placed on your servers (created by you) that must perform the operations necessary to launch the container. By clicking this option, the “**Set as deployed and call the URL**” synchronization mode will be proposed in the “**DEPLOY**” step.
* **Manual**: this mode allows you to load the container directly from the interface so that you can then deploy it manually on your site. You can check the “**Add unminified version**” function in order to load the container in either compressed (minified) or uncompressed (unminified) mode. By clicking this option, the “**Set as deployed and get JavaScript file**” synchronization mode will be proposed in the “**DEPLOY**” step.
* **Send an email**: this deployment mode complements the other 4 modes. It is used to send a notification email to specified users when a deployment is carried out.

Recurring synchronization:

Recurring synchronization is used to automatically deploy a container on a regular basis via the deployment mode desired (FTP, batch or send by email).

Two programming modes are available: Simplified mode and expert mode:

* “Simplified mode”: Simplified mode is used to program recurring synchronization by the day and hour (e.g. recurring synchronization every day at 2 p.m.).
* “Expert mode”: Expert mode is used to program recurring synchronization with more precision, by minute, hour, day, week and month (e.g. recurring synchronization every two weeks of the month on Tuesdays at 11:35 a.m.).

<figure><img src="../../../../../../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

### **Advanced**

<figure><img src="../../../../../../../.gitbook/assets/image (106) (1).png" alt=""><figcaption></figcaption></figure>

**NoScript support**: This option is used to create a noscript version of the container that allows both the container and its tags to execute for users without JavaScript activated on their browser.

You can also define a JavaScript version and noscript version for each tag.

**Verification by MD5 file:** This option is linked to the “Manual” deployment mode and associates an MD5 code with a container version in either compressed (minified) or uncompressed (unminified) mode in order to verify the integrity of the container before putting it into production. It does this by comparing TagCommander’s MD5 code with the MD5 code calculated by your technical team upon receiving the container.

**Include jQuery (at the test step):** This option allows you to include the JavaScript jQuery library in the test step so that you won’t have any errors linked to its absence if it is indeed present on your site.

**Display block for old tc\_event function:** This option allows to show/ hide the old TagCommander event section. It is hidden per default.

**Default expiration date:** This option allows you to set a default expiration date for all the tags to be added to the container (in this case, the tags will be deactivated). If necessary, it also allows you to send an expiration report to selected users when a tag expires (the report is sent 2 weeks and 1 week before the tags expire).

**Container default trigger:** Container Load is the value by default, you can modify it if needed

**Linked sub-domain(s) for Phoenix:** Enter your sub-domains for Phoenix, which enables you to persist 1st party cookies for longer durations to reduce the impact of ITP on your website and business.

**Force Cookie SameSite setting:** all cookies created through the container will get the SameSite parameter

**Force Cookie Secure setting:** all cookies created through the container will get the Secure parameter



\*Note: this setup can be modified at any time.\
Simply click the 'parameter' icon:\


<figure><img src="../../../../../../../.gitbook/assets/image (112) (1).png" alt=""><figcaption></figcaption></figure>

