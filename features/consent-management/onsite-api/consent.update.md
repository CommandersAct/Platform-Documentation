---
description: Method to update Commanders Act consent status OnSite via JavaScript.
---

# consent.update

{% hint style="info" %}
The Commanders Act [OnSite API stub](getting-started.md) has to be installed before using any of the OnSite API functions.
{% endhint %}

```javascript
cact('consent.update', consentObject)
```

The `consent.update` method allows to update the consent with JavaScript. It has to be called with a Consent Object that includes the updated settings. Commanders Act will deep merge the status fields of the current Consent Object with the provided object and automatically update all meta properties and the `consent.status` property automatically. In case a `consent.status` field is provided with value **all-on,** **all-off** or **unset** all other updates are ignored and all categories and vendor settings will be set to **on**, **off** or **unset** accordingly.

All not configured categories and vendors are ignored when deep-merging the consent objects.

## Examples

### Update categories and vendors

```javascript
cact('consent.update', {
    categories: {
        '2': { status: 'on' }
    },
    vendors: {
        '1': { status: 'on' }
    }
});
```

Below you can see how the Consent Object is affected by this update.

```javascript
/* Consent Object Before Update
{
    meta: { ... },
    consent: {
        status: "mixed",
        categories: {
            "1": { status: "on" },
            "2": { status: "off" }
        },
        vendors: {
            "1": { status: "off" },
            "2": { status: "on"}
        }     
    }
}
*/

// Update
cact('consent.update', {
    categories: {
        '2': { status: 'on' }
    },
    vendors: {
        '1': { status: 'on' }
    }
});

/* Consent Object After Update
{
    meta: { ... }, // automatically updated
    consent: {
        status: "all-on", // automatically updated
        categories: {
            "1": { status: "on" },
            "2": { status: "on" } // updated
        },
        vendors: {
            "1": { status: "on" }, // updated
            "2": { status: "on"}
        }     
    }
}
*/
```

### Update IAB **TCF/ACM** categories and vendors

```javascript
cact('consent.update', {
    categories: {
        '1': { // non-IAB category
            status: 'on' 
        },
        'tcf2_1': { // TCF purpose 1
            status: 'on' // no legintStatus for purpose 1
        },
        'tcf2_2': { // TCF purpose 2
            status: 'off',
            legIntStatus: 'on'
        },
        'tcf2_sf_1': { // TCF special feature 1
            status: 'on'
        }
    },
    vendors: {
        'tcf2_1': { // TCF vendor 1
            status: 'on',
            legIntStatus: 'off'
        },
        'tcf2_2': { // TCF vendor 2
            status: 'on',
            legIntStatus: 'on'
        },
        'acm_1': { // ACM vendor 1
            status: 'on'
        }
    }
});
```

### **Accept all categories and vendors**

```javascript
cact('consent.update', { 
    status: 'all-on'
});
```

Specifying a category or vendor will not have any effect.&#x20;

```javascript
cact('consent.update', { 
    status: 'all-on', 
    categories: {
        '2': { status: 'unset' } // ignored as global status is specified
    }
});
```

Below you can see how the Consent Object is affected by this update.

```javascript
/* Consent Object Before Update
{
    meta: { ... },
    consent: {
        status: "unset",
        categories: {
            "1": { status: "unset" },
            "2": { status: "unset" }
        },
        vendors: {
            "1": { status: "unset" },
            "2": { status: "unset"}
        }     
    }
}
*/

// Update Method
cact('consent.update', { 
    status: 'all-on'
});

/* Consent Object After Update
{
    meta: { ... }, // automatically updated
    consent: {
        status: "all-on",
        categories: {
            "1": { status: "on" }, // automatically updated
            "2": { status: "on" } // automatically updated
        },
        vendors: {
            "1": { status: "on" }, // automatically updated
            "2": { status: "on"} // automatically updated
        }     
    }
}
*/
```

### **Refuse all categories and vendors**

```javascript
cact('consent.update', { 
    status: 'all-off'
});
```

Specifying a category or vendor will not have any effect.&#x20;

```javascript
cact('consent.update', { 
    status: 'all-off', 
    categories: {
        '2': { status: 'on' } // ignored as global status is specified
    }
});
```

Below you can see how the Consent Object is affected by this update.\
**Note:** required categories are not affected.

```javascript
/* Consent Object Before Update
{
    meta: { ... },
    consent: {
        status: "mixed",
        categories: {
            "1": { status: "on" },
            "2": { status: "off" },
            "3": { status: "on", required: true }
        },
        vendors: {
            "1": { status: "on" },
            "2": { status: "on"}
        }     
    }
}
*/

// Update Method
cact('consent.update', { 
    status: 'all-off'
});

/* Consent Object After Update
{
    meta: { ... }, // automatically updated
    consent: {
        status: "all-off",
        categories: {
            "1": { status: "off" }, // automatically updated
            "2": { status: "off" }, // automatically updated
            "3": { status: "on", required: true } // unchanged
        },
        vendors: {
            "1": { status: "off" }, // automatically updated
            "2": { status: "off"} // automatically updated
        }     
    }
}
*/
```

### Specify update action

You can specify an action inside the update parameters:

```javascript
cact('consent.update', {
    action: 'banner_button',
    categories: {
        '2': { status: 'on' }
    },
    vendors: {
        '1': { status: 'on' }
    }
});
```

This action value will be used to compute your dashboard metrics.\
If it is omitted, the default value is `banner_button`.

The allowed values are:

* banner\_button
* pc\_save
* page\_click
* scroll
* browse

Additionally, the following values are allowed for optout only (`status: 'all-off'` ):

* banner\_cross
