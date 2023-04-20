# Deployment and roll back

A container can be deployed at the “**DEPLOY**” step:&#x20;

<figure><img src="../../../../../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

Before deploying a container version, you can:

* Display all the modifications made to your container since its last deployment (technical logs) (1) in the “**MODIFICATIONS SINCE LAST DEPLOYMENT**” section
* View the history of generated versions in the “**DEPLOY BY VERSION**” section.

For each version generated, you will find his version number, creation date, status (“deployed” when it is the version currently deployed and/or “live” when it is the version currently called for the site) , the name of the person who generated the version, a comment, and the container’s size. You will also be able to load your selected container version directly from the interface  or via a permanent link:

<figure><img src="../../../../../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

Additional information:

The “Weight Detail” section shows the container’s size (in GZIP format), its change in size since the last deployment as well as the percentage of space occupied by each of the following container elements:

* Core: The weight of the content necessary to execute the container
* Tags: Tags’ weight
* Events: Events’ weight
* Rules: Rules’ weight
* Privacy: Privacy module’s weight (if activated)
* Internal variables: Internal variables’ weight
* Deduplication channel: Deduplication channel’s weight (if activated)

<figure><img src="../../../../../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

Deploying a new container version or rolling back a container is done in two steps:

* Choose the version to deploy.

Note: to roll back the container, just select a previous container version.

* Choose the deployment method.

Note: the deployment method depends on your container’s hosting and synchronization, which are defined at the project’s start with your personal consultant.

<figure><img src="../../../../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

Once the version and deployment method are selected, a window summarizing the deployment will appear. Click “**Deploy**” to validate:

<figure><img src="../../../../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Additional information

Depending on the hosting and synchronization methods defined at the project’s start and configured in the interface, different deployment options are available in the drop-down menu under “Choose the deployment method”:

<figure><img src="../../../../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>
