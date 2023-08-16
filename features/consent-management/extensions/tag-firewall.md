---
description: TagFirewall can whitelist or blacklist tags.
---

# Tag Firewall

{% hint style="info" %}
TagFirewall is a paid extension that can be installed with Commanders Act TMS or run in standalone mode. Please contact a Commanders Act consultant or account manager to activate it.
{% endhint %}

## Overview

TagFirewall blocks unauthorized tags (domains) in real time. This can e.g. help to block and reduce the risk of piggybacking tags. TagFirewall is highly dynamic and can therefore enrich an existing Content Security Policy (CSP) setup to resolve critical issues with tags in minutes or replace the need for a Content Security Policy (CSP) entirely. TagFirewall offers two modes:

### Blacklist Mode

This mode blocks tag communication with a configurable list of domains. Communication with all other domains is still permitted.

### Whitelist Mode

This mode blocks tag communication with all domains except a configured whitelist.

## Setup

### Commanders Act

TagFirewall can be set up and configured with the tag template "Commanders Act - TagFirewall" in Commanders Act TMS tag library.

| Option                | Description                                                                                                                                               |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Mode**              | Allows to select Blacklist or Whitelist mode.                                                                                                             |
| **Blacklist domains** | Domains that should be blacklisted. Enclosed in `"` and and separated by`,` . (_Only for Blacklist Mode_)                                                 |
| **Internal domains**  | Tag domains that should be whitelisted. Enclosed in `"` and and separated by`,` . (_Only for Whitelist Mode_)                                             |
| **Tag domains**       | Internal domains (domain the website needs to function) that should be whitelisted. Enclosed in `"` and and separated by`,` . (_Only for Whitelist Mode_) |
| **Check SSL**         | This option allows to block all `http` script hits (it will only allows `https` script hits).                                                             |

<figure><img src="../../../.gitbook/assets/image (160).png" alt=""><figcaption><p>Example of a TagFirewall configuration.</p></figcaption></figure>

### Standalone

TagFirewall can be set up and configured with a custom JavaScript tag for all other installations. The tag has following options.

| Option                     | Description                                                                                                                  |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **\<whitelist\_tags>**     | Array of domains used by tags that should not be blocked. (_Only for Whitelist Mode_)                                        |
| **\<whitelist\_internal>** | Array of internal domains (domain the website needs to function) that should not be blocked. (_Only for Whitelist Mode_)     |
| **\<blacklist\_tags>**     | Array of domains used by tags that should be blacklisted. (_Only for Blacklist Mode_)                                        |
| **\<active\_flag>**        | This option activates TagFirewall. Set to `true` to activate TagFirewall.                                                    |
| **\<check\_ssl>**          | This option allows to block all `http` script hits (it will only allows `https` script hits). Set to `true` to activate it.  |
| **\<script\_url>**         | URL of the TagFirewall library JavaScript file. This URL will be provided by a Commanders Act Consultant or Account Manager. |

{% tabs %}
{% tab title="Blacklist Mode" %}
```markup
<script>
tC = tC || {};
tC.tagFirewall = tC.tagFirewall || {};

tC.tagFirewall.list = {
    "blacklist": {
        "tags": <blacklist_tags>
    }
};

tC.tagFirewall.checkSSL = <check_ssl>;
tC.tagFirewall.blocked  = <active_flag>;  
</script>
<script src="<script_url>"></script>
```
{% endtab %}

{% tab title="Whitelist Mode" %}
```markup
<script>
tC = tC || {};
tC.tagFirewall = tC.tagFirewall || {};

tC.tagFirewall.list = {
    "whitelist": {
        "internal": <whitelist_internal>,
        "tags": <whitelist_tags>
    }
};

tC.tagFirewall.checkSSL = <check_ssl>;
tC.tagFirewall.blocked  = <active_flag>; 
</script>
<script src="<script_url>"></script> 
```
{% endtab %}
{% endtabs %}

#### Examples

{% tabs %}
{% tab title="Blacklist Mode" %}
```markup
<script>
tC = tC || {};
tC.tagFirewall = tC.tagFirewall || {};

tC.tagFirewall.list = {
    "blacklist": {
        "tags": ["bad-domain1.com", "bad-domain2.com"]
    }
};

tC.tagFirewall.checkSSL = true;
tC.tagFirewall.blocked  = true;  
</script>
<script src="<script_url>"></script>
```
{% endtab %}

{% tab title="Whitelist Mode" %}
```markup
<script>
tC = tC || {};
tC.tagFirewall = tC.tagFirewall || {};

tC.tagFirewall.list = {
    "whitelist": {
        "internal": ["cdn.yourdomain.com", "cdn.yourdomain2.com"],
        "tags": ["facebook.com","twitter.com"]
    }
};

tC.tagFirewall.checkSSL = true;
tC.tagFirewall.blocked  = true;
</script>
<script src="<script_url>"></script>
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
The tag should be included in the `<head>` of your document. It can only block tags that are loaded **after** the TagFirewall tag and JavaScript library file.
{% endhint %}
