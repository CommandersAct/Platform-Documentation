# Identity resolution

Identity resolution (Fuse) is our **live identity reconciliation feature**. Your customers are using many devices, switching from one channel to another (web, mobile, shops, ads…) and would like a personalized experience across all these devices/channels.

For example, a customer can visit your website during the day with his laptop, then click on an ad and come back later to buy with his mobile phone and contact the customer service 2 days after.

On your side it is difficult to unify all these actions around one and unique user because it is stored in many systems: your CRM, your website, your ad agency, your customer service system…\
This is why we launched Fuse, in order to help you to **create a complete view of your customers**. Our **real-time proprietary reconciliation algorithm**, Fuse, is the core of our CDP (Customer Data Platform) that can help you to define the most suitable audience segments and better activate them.

![](<../.gitbook/assets/image (9).png>)

## What is Fuse V1, and what are the differences between V1 and V2?

On **Fuse V1,** our goal was to **identify** same users and **duplicate** for each visitor (cookie) all the data we collected.\
For example, we collected data about a visitor A with a laptop and a visitor B with a mobile phone. If, with our algorithm, we noticed that visitor A = visitor B, we duplicate the information from visitor B to visitor A and vice-versa. So we can have an overview of visitors who shared the same information and are linked.

![](<../.gitbook/assets/image (11) (2).png>)

With **Fuse V2,** we decided to go further by **merging** these visitors in order to have a **unique user** with all the data collected. With Fuse V2, the goal is to detect with multiple reconciliation keys the same customer and unify all the data around 1 unique user in order to have a complete view of the customer across all devices and all channels.

![](<../.gitbook/assets/image (12).png>)

With Fuse V2 our CDP become **user-centric** rather than cookie centric and that change the way you define your marketing campaigns: you don’t talk to devices anymore but to humans directly, to users.

## How Fuse V2 works?

Technically, Fuse V2 use **reconciliation keys** in order to match the data according to variables defined. These keys could be an email address, a personal ID, a phone number, a postal address…

For now only 1 key is managed, but later you will be able to define multiple keys and prioritize its. For example, you can define that the main key is the email address and, if there is no email address, the second key to check is the phone number or whatever you feel relevant for you and your business.

A merge between 2 users will happen if a match is detected because the reconciliation key is the same for the 2 users (email address, for example). The newest user is merged into the oldest one. The data collected for the newest user is stored on the oldest one, and the newest user is deleted.

![](<../.gitbook/assets/image (7) (2).png>)

Every document on visitor B (conversions, page views, impressions, clicks, consents…) are moved to user A. There is no data deleted, only the user is deleted, and information are moved to the main user (A in our example).

{% hint style="info" %}
Technically speaking, we have the **tcid** (cookie ID) to identify **devices,** **PID** (personal identifier) to identify **users** and **user\_id** to identify users based on a key coming from our customers (**CRM ID** for example).

**tcid = devices**\
**pid = users**\
**user\_id = users (key from customer)**
{% endhint %}

## What happens for consents?

When we will operate a merge, we will take into consideration the latest consents recorded in order to respect users’ choices.

## What happens for Augmented User Attributes?

[Augmented user attributes](enrichments/augmented-user-attributes/) (sum, min, max, count, calculus...) are automatically recalculated when a merge occurs.

## How do we manage shared devices?

Some devices are strictly personal, like mobile phones, but others could be shared like tablets. For example, in a family, the husband can use the tablet and 1 hour later the wife can use also the tablet. We are able to identify this behavior with FuseCommander.

As soon as we detect a new reconciliation key (login, email address, user\_id) different from the previous session on the device, we can distinguish different users and address the right user.

![](<../.gitbook/assets/image (10).png>)

On case 1 (left) we can't identify a new user because there are no reconciliation keys (no login, no email...). On contrary, on case 2 (right), there is a login, so we can create a new user or update an existing user. As a result, the tcid (cookie identifier) stays the same but the pid (personal identifier) is different as well as the user\_id.

## How do we manage Wi-Fi public hotspots?

On public hotspots, many devices share the same IP address, they are connected on the same network. How to avoid having 1 unique user for all these devices?

Technically speaking, we don't consider on the same way users on Chrome / Android and users on Safari / iOS.

On Chrome / Android, we are able to create 1 user per device, with different pid (Personal Identifier) because the tcid (=cookie identifier) is different.

As soon as we can identify 2 devices with the same user\_id (login for example), we can merge these 2 users with Fuse V2, to have 1 unique user for these 2 devices.

![](<../.gitbook/assets/image (14) (1).png>)

For Safari / iOS, it is different because we can't have different tcid. Due to cookie limitations on Safari, we use a fingerprint. Unfortunately, on a public hotspot, all devices have the same IP address and, as a result, the fingerprint is the same, meaning we have 1 unique user for all these devices.

However, as soon as we can detect that a user is unique (with a login for example), we can create a separate user.

![](<../.gitbook/assets/image (13).png>)
