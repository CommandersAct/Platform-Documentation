# Migration to Data Manager API

## Connect your Google account to the Data Manager API

{% hint style="danger" icon="triangle-exclamation" %}
**Do not remove your existing Google Ads permissions or credential.** Only add the new permissions requested below, as removing your current access will break your existing connections.
{% endhint %}

Google is replacing the Google Ads API with the Data Manager API. To keep your Google connections running smoothly, add a new Google credential in Commanders Act.

{% hint style="info" %}
**This updates your existing credential: it is never removed.** Your current connections stay active throughout the process.&#x20;

Estimated time: less than 2 minutes.
{% endhint %}

## Before you start: check your access rights

You'll need two levels of access to complete this:

* **In Commanders Act**: access to `Administration > Connector Credentials`. If you don't see this menu, ask your Commanders Act administrator to grant you access or to perform this update on your behalf.
* **In Google**: sufficient rights on the Google Ads account to grant API access (typically Admin access on the Google Ads account, or on the Google Workspace/Google account used to sign in). If you're not sure who manages this on your side, check with whoever originally set up your Google Ads connection.

{% hint style="warning" %}
If you sign in with a Google account that doesn't have the right permissions, the consent screen may not show all the expected permissions, or the connection may fail. In that case, ask your Google Ads administrator to complete this step instead.
{% endhint %}

## Step-by-step tutorial

### Step 1 — Go to Connector Credentials

In Commanders Act, go to `Administration > Connector Credentials`, then click **Add connector credentials** in the top right corner.

<figure><img src="../../../../.gitbook/assets/step3-consent-summary.png" alt=""><figcaption></figcaption></figure>



### Step 2 — Select Google Ads

In the connector list, select **GoogleAds**.



<figure><img src="../../../../.gitbook/assets/step2-select-googleads.png" alt=""><figcaption></figcaption></figure>

### Step 3 — Sign in with Google

A Google window opens asking you to sign in and grant access to CommandersAct. Review the summary, then click **Continue**.

Google may then show the detailed list of permissions requested.

{% hint style="warning" %}
**Accept all the permissions shown**, even if some look broader than what you expect to use. Do not uncheck or skip any permission on this screen as declining one can break part of your Google connection later.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/step1-connector-credentials (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/step4-scopes-detail (1).png" alt=""><figcaption></figcaption></figure>

### Step 4 — Select your Google Ads account

Once access is granted, select the Google Ads account(s) you want to link, then click **Save**.

If several Google Ads accounts are already connected to your Commanders Act account, select all the accounts you want to update: this will update the scope for all the accounts you select.

<figure><img src="../../../../.gitbook/assets/step5-select-account.png" alt=""><figcaption></figcaption></figure>

### Step 5 — You're done

Your Google credential is now updated for the Data Manager API. Your existing connections and destinations continue to run without any further action on your side.

## FAQ

**Will this delete my current Google connection?**

No. This action updates your existing credential in place. Nothing is deleted, and your current connections keep running during the update.

**What happens if I don't do this?**

Google is phasing out the Google Ads API in favor of the Data Manager API. Without this update, your Google Ads connections may stop working once Google fully retires the old API.

In addition, some future Google destinations will require the Data Manager API to run — you won't be able to use them until you complete this upgrade.

**Why do I keep both my Google Ads and Data Manager permissions?**

Google hasn't migrated every feature to the Data Manager API yet — some parts of the Google Ads connection still rely on the older API. Keeping both active ensures nothing breaks while Google completes this transition on their end.

**I only see some permissions, not "Data Manager" by name. Is that normal?**

Yes. Google's consent screen may not always list a permission named exactly "Data Manager". What matters is that you accept every permission shown on the screen, without unchecking any of them.

**Can several people in my company do this?**

Yes, this update can be repeated per user/account. See Before you start for the access rights required on both sides.
