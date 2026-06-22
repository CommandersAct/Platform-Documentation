# Profile Explorer

The Profiles section lets you explore the individual users unified in your CDP.&#x20;

It has two pages:&#x20;

* **Profile Explorer**: a listing of all unified users, with statistics, filters and search.&#x20;
* **Unified Profile:** a detailed, read-only card for a single user, organized into four tabs: Identities, Segments, Activities and Attributes.&#x20;

Both pages are read-only: no data can be edited or deleted from this section. They are designed to explore and verify data - for example to check how a user is identified, segmented, enriched and tracked.

{% hint style="info" %}
This is the first version of Profiles. More capabilities will be added over time.
{% endhint %}

Availability and permissions Profiles is available to clients on the CDP offer.&#x20;

Access is governed by two separate permissions, because the Unified Profile exposes sensitive personal data:&#x20;

* Profile Explorer: access to the listing&#x20;
* Unified Profile: access to the detailed user card&#x20;

A user can be granted the Profile Explorer without the Unified Profile.&#x20;

Default access by system profile:&#x20;

| Profile       | Profile Explorer | Unified Profile |
| ------------- | ---------------- | --------------- |
| Administrator | Yes              | Yes             |
| Technical     | Yes              | Yes             |
| Marketing     | Yes              | Yes             |
| Read-only     | Yes              | No              |

For custom profiles, the two permissions are set independently under the Profiles permission section (Yes/No each).

{% hint style="info" %}
Consider that the Profile Explorer and Unified Profile pages include read permissions for variables, segments and user-attributes.
{% endhint %}

## Accessing Profiles&#x20;

In the main menu, go to **Customers** > **Profiles** > **Profile Explorer**. Select a user to open their Unified Profile.&#x20;

## Profile Explorer

The Profile Explorer shows all unified users, ordered by most recent activity. Use the search field - Search by ID, name or email - to find a specific user. The last filter applied is kept while you navigate within the same account, and the listing is paginated.

{% hint style="info" %}
Activity is any interaction with the brand (website, app, offline). Technical actions - such as entering or leaving a segment, or device reconciliation - are not counted as activity.
{% endhint %}

### Statistics banner

A banner summarizes the population currently displayed. The figures update when filters are applied:

* Total number of user
* Identified users (count and % of total)
* Reconciled users - cross-device (count and % of total)
* Active users - activity in the last 30 days (count and % of total)
* Purchasing users - order in the last 30 days (count and % of total)

### Columns

* Status - a green (active) or grey (inactive) dot. A user is active when an activity is recorded in the last 30 days
* Main identifier - the PID for anonymous users, name and email for identified users
* Devices - icons of the user's reconciled devices
* Consent
* Last activity - date and nature of the activity
* Last order - amount and date
* Segments

### Filters

* Identity - All (default), Identified, Anonymous
* Activity - All (default), Active, Inactive
* Segment - the account's segments; none selected by default
* Device - All (default), Desktop, Tablet, Mobile
* Consent - categories. When sub-categories exist, there are displayed below the main categories. IAB categories are not included in this version.

## Unified Profile

The header shows an Identified/Anonymous badge, an Active/Inactive badge, the user's main identifier and a link back to the listing. The profile is organized into four tabs.

### Identities

Basic information is displayed in three rows:

* User ID, full name, email
* Master ID - the user's PID
* Phone, postal address, birthday

Each field is fed by a CDP variable.&#x20;

{% hint style="warning" %}
When no value is mapped, the field shows _Unmapped / Unspecified variable_ - a reminder to follow the Commanders Act normalized mapping so the profile populates correctly.\
If the value is not specified for a user (not sent), the field will also show _Unmapped / Unspecified variable_.
{% endhint %}

| Field               | Variable(s) used                                                             |
| ------------------- | ---------------------------------------------------------------------------- |
| User ID             | `user_id`                                                                    |
| First name          | `person.first_name`, `person.firstname`                                      |
| Last name           | `person.last_name`, `person.lastname`                                        |
| Email               | `user_email`, `person.email`                                                 |
| Phone               | `person.phone`, `phone`                                                      |
| Postal address      | `person.address`, `address`, `person.city` / `state` / `zipcode` / `country` |
| Birthday            | `person.birthday`, `person.birthdate`                                        |
| Consent categories  | `user_privacy_categories`                                                    |
| Top page categories | `env_template`                                                               |

The tab also includes:

* Devices - identified devices.
* Consent categories - for each category, it can be clearly seen if consent was given or not. Main categories are shown by default and can be expanded to display sub-categories
* Top page categories - a donut chart of the most viewed page categories over the last 30 days, shown as percentages
* Engagement score (LAB) - a score out of 100 split into three levels (low, medium, high)
* Monthly revenue - revenue per month over the last 6 months

{% hint style="info" %}
About the engagement score: it is based on the RFM model (Recency, Frequency, Monetary), a standard marketing framework that rates a user's behavioral value on three axes: how recently they were active, how often they buy and browse, and how much they have spent. These three axes are combined into a single score from 0 to 100, then mapped to three levels: High (70 and above), Medium (40 to 69) and Low (below 40).

This score is currently under beta version (indicated by the LAB label)
{% endhint %}

{% hint style="info" %}
If the Conversion Universe is not activated, the Monthly Revenue widget is not available. The engagement score calculation is also affected if this universe is not activated.
{% endhint %}

### Segments

Lists all the segments the user belongs to, with the number of users and the associated destinations. Segments with an active destination are shown first. Select a segment to open it. To create and manage segments, see Segment.

### Activities

* First activity - the oldest date between the first visit and the first order, with its nature and date
* Last activity - the most recent date between the last visit and the last order, with its nature and date
* Last 30 days - statistics for page views, product views and purchases, plus the top page categories
* Activity timeline (last 30 days) - events grouped by session : date, action, and the count of page views, product views and purchases, with page titles for page views. The latest session is shown; the rest can be expanded
* Purchase history (all time) - total purchases and revenue, first order, and last order with its amount and date.
* Last 6 months - number of orders, total revenue and average order value (AOV)
* Revenue chart - monthly revenue as bars and monthly AOV as a line over the last 6 months

{% hint style="info" %}
If the Conversion Universe is not activated, the Purchase section is not available.
{% endhint %}

### Attributes

Lists the Augmented User Attributes computed for the user, grouped by type and displayed in this order: Flags, Boolean, Rolling Count, Rolling Sum, Calculus, Copy. The 5 most recently created or modified attributes of each type are shown by default; expand a type to see the others. A search field helps locate a specific attribute.<br>

## Benefits

* See, in one place, all the data the CDP unifies for a given user
* Validate that a user is correctly identified, reconciled, segmented and qualified for a campaign
* Investigate a user journey
* Explore audience composition from the Profile Explorer and its statistics
