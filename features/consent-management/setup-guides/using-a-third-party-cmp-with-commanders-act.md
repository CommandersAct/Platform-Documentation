# Using a Third-Party CMP with Commanders Act

If you manage cookie consent with a **Consent Management Platform (CMP) other than the Commanders Act CMP**, there's one small piece of setup needed to keep your data collection GDPR-compliant. It takes just a few minutes to implement and doesn't require any changes to your page load or reload behavior.

This modification will impact data collection for Deduplication, Cookie Sync and Phoenix

### Why this is needed

Commanders Act modules need to know, in real time, whether a visitor has given consent to cookies. When you use your own CMP or an external one(such as UserCentrics, OneTrust, etc...), we don't have direct visibility into that consent status — so you'll need to expose it to us through a simple variable in your datalayer.

Once this variable is in place, your setup will be fully GDPR-compliant and ready to use across all impacted modules.

### What you need to add

Add the following variable to your datalayer:

```
tc_vars.external_consent_status
```

**Expected behavior:**

| Situation                         | Value   |
| --------------------------------- | ------- |
| Default / no decision yet         | `false` |
| Visitor accepts cookies (opt-in)  | `true`  |
| Visitor refuses cookies (opt-out) | `false` |

That's it — just a boolean that reflects the current consent state.

### When it should update

This is the key point to get right: the variable must update **instantly, without a page reload**, right at the moment the visitor makes a consent choice on your banner — and just **before** the Commanders Act container reloads.

In practice, this means your CMP's consent callback (the code that runs when a visitor clicks "Accept" or "Reject") should update `tc_vars.external_consent_status` first, then let the container reload happen as usual.

### Final step: regenerate your containers

Once the variable is implemented on your site, you'll need to **regenerate all your containers** on the platform. This step activates the change in production — without it, your containers will keep running with the previous configuration.

Go to your container list on the platform and regenerate each one. No further configuration is required on our side.

### What this impacts

This setup affects three modules, which will now correctly respect your visitors' consent choices:

* **Deduplication**
* **Cookie Sync**
* **Phoenix**

### Quick checklist

* \[ ] Added `tc_vars.external_consent_status` to the data layer
* \[ ] Verified it defaults to `false`
* \[ ] Verified it switches to `true` on opt-in, and stays `false` on opt-out
* \[ ] Verified it updates before the container reloads (no page refresh needed)
* \[ ] Regenerated and deploy all containers on the platform

Once these boxes are checked, you're all set — no further action needed.

Result expected on states "before consent" and "after refuse" (optout): \
No Deduplication cookies, no Phoenix cookies, no Local Storage for Cookie Sync are set on your browser
