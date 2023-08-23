# Copy Management

## Introduction

&#x20;The “**Copy Management**” user interface is available to administrators only, from the “**Administration**” menu:

<figure><img src="../../../../../../.gitbook/assets/image (363).png" alt=""><figcaption></figcaption></figure>

It allows **duplicating** sites, containers, variables, deduplication settings and tags.



## _Copying a site_



Follow these steps to copy an existing site and its contents:

1/ **“Element to copy”**: select “Site” from the drop down menu to duplicate a site.

2/ **“Site to copy”**: select the site you wish to duplicate.

3/ “**Add several new sites based on the site to copy”**: If you wish to copy the content of a given site to another one and only, select “No”. If you wish to copy that site’s content to more than one site, select “Yes”.

4/ **“Site name”**: enter the name(s) of your new site(s). The “+” and “–“icons allow adding or deleting sites.

5/ **“Grant same rights to the same user(s) on the new site(s)”**: If you wish to duplicate user access from one site to another click “Yes”, otherwise click “No” (should you click “No”, no one else but you will have access to the duplicated site).

6/Click the “**COPY**” button to validate your settings.

<figure><img src="../../../../../../.gitbook/assets/image (364).png" alt=""><figcaption></figcaption></figure>

**What elements are duplicated with the “Site Copy” feature?**

The “Site Copy” feature duplicates the following elements and creates one or more new sites with the exact same settings as the source site:

* **Commanders Act TMS**:
  * Containers
  * Tags
  * Events
  * “Static JavaScript Code” and “Dynamic JavaScript code” files
  * Rules
  * Data layer (external, internal and event variables)
  * Deduplication settings
  * Privacy settings (if the module is activated)
* **Commanders Act Campaign**:
  * Attribution models
  * Segments
  * Excluded IPs
  * Channel identification
  * Dimensions (conversion/traffic)
  * Currencies
  * Costs
* **Commanders Act Segments**
  * Segments
  * Streams
* Cross-product options: connectors

The “**Site Copy**” feature does not duplicate these items:

* **Commanders Act TMS**:
  * Generated container versions
* **Commanders Act Campaign**:
  * Custom reports
  * Raw data
* **Commanders Act Segment**:
  * Raw data

## Copying a container

_Note: only administrators and technical users can copy sites_

Follow these steps to copy an existing container and its contents:

1\) – Click the “Admin” tab

2\) – Click the “Copy Management” tab

3\) – Select “Container” from the dropdown menu\


<figure><img src="../../../../../../.gitbook/assets/image (365).png" alt=""><figcaption></figcaption></figure>

4\) – Select the site the container you want to duplicate belongs to

5\) – Select the container to copy

6\) – Select the site to host the duplicated container (among the sites you manage)

7\) – Choose whether you want to create a new container or replace an existing container with the duplicate

8\) – Name the copy

9\) – Click “Copy”

<figure><img src="../../../../../../.gitbook/assets/image (366).png" alt=""><figcaption></figcaption></figure>

## Copying tags

_Note: only administrators and technical users can copy tags_

{% hint style="info" %}
The copy tag functionality is also available on the deploy step of containers for admin users (can be added to custom profiles with Profile Management).
{% endhint %}

Follow these steps to copy tags from a given container:

1\) – Click the “Admin” tab

2\) – Click the “Copy Management” tab

3\) – Select “Tag” from the drop down menu

4\) -Select the site containing the tags you wish to copy

5\) – Select the container the tags are in

6\) – Select the tag(s) to copy

7\) – Select the destination site

8\) – Select the destination container

9\) – Click the “+” button to add more destination sites and containers

10\) – Click copy

<figure><img src="../../../../../../.gitbook/assets/image (367).png" alt=""><figcaption></figcaption></figure>

## Copying variables

_Note: only administrators and technical users can copy variables_

Follow these steps to copy existing variables:

1\) – Click the “Admin” tab

2\) – Click the “Copy Management” tab

3\) – Select “Variables” from the drop down menu

4\) – Select the site containing the variables you wish to copy&#x20;

5\) –  Select the variables to copy

6\) – You will see the number of selected variables

7\) – Add the site in the drop down menu&#x20;

8\) – You can add more destination sites if needed

9\) – Click “copy”

<figure><img src="../../../../../../.gitbook/assets/image (368).png" alt=""><figcaption></figcaption></figure>

## Copying tag librairies

_Note: only administrators and technical users can copy tag librairies (to learn more about the libraries’ customization options, please click_ [_here_](https://community.commandersact.com/en/customizing-the-tag-library-whitelisting-tags/)_)_

Follow these steps to copy tag librairies:

1\) – Click the “Admin” tab

2\) – Click the “Copy Management” tab

3\) – Select “Tags Library” from the dropdown menu

4\) – Choose the site containing the tag whitelist to copy

5\) – Select one or more destination sites

6\) – Click “Copy”\


<figure><img src="../../../../../../.gitbook/assets/image (369).png" alt=""><figcaption></figcaption></figure>

## Copying deduplication settings

_Note: only administrators and technical users can copy deduplication settings_

Follow these steps to copy existing deduplication rules:

1\) – Click the “Admin” tab

2\) – Click the “Copy Management” tab

3\) – Select “Deduplication Configuration” from the dropdown menu

4\) – Choose the site containing the deduplication configuration to copy

5\) – Select on or more destination sites

6\) – Click “Copy”\


<figure><img src="../../../../../../.gitbook/assets/image (370).png" alt=""><figcaption></figcaption></figure>

## Copying rules

Follow these steps to copy rules from one container to another (or within the same container):

1\) Click the “Admin” tab

2\) Click the “Copy Management” tab

3\) Select “_Rules”_ from the drop down menu displaying all the possible elements to copy:

4\) Select the site and the container you wish to copy rules from:

5\) Select the rules you wish to duplicate from the “perimeter” or “constraint” sections:

6\) Select the target site and container from the drop down menu:

7\) Click copy\


<figure><img src="../../../../../../.gitbook/assets/image (371).png" alt=""><figcaption></figcaption></figure>
