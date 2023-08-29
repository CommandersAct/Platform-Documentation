# Campaign Tracking events

## ad\_view

This event is associated with your ad being displayed, can be used to track the touch point "impressions" in Campaign Analytics module

## ad\_click

This event is associated with someone clicking your ad, can be used to track the touch point "clicks" in Campaign Analytics module



#### Parameters <a href="#parameters_35" id="parameters_35"></a>

<table><thead><tr><th width="161">Name</th><th width="100">Type</th><th width="85">Required</th><th width="153">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>ad_cost_id</code></td><td><code>string</code></td><td>No</td><td>1254965</td><td>replace the <code>tclid</code> from MixCommander</td></tr><tr><td><code>user</code></td><td><a href="campaign-analytics-module-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>ad_format</code></td><td><code>string</code></td><td>No</td><td>image</td><td>Ad type/format</td></tr><tr><td><code>campaign</code></td><td><code>string</code></td><td>No</td><td>my_campaign</td><td>campaign name</td></tr><tr><td><code>keyword</code></td><td><code>string</code></td><td>No</td><td>t-shirt</td><td>keywords of the campaign</td></tr><tr><td><code>medium</code></td><td><code>string</code></td><td>Yes</td><td>seo</td><td>medium of touch point</td></tr><tr><td><code>source</code></td><td><code>string</code></td><td>Yes</td><td>my_source</td><td>source of touch point</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger','ad_click', { /*or ad_view*/
    "medium": "seo",
    "campaign": "my_campaign",
    "source": "my_source",
    "keyword": "t-shirt",
    "ad_format": "image"
}
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}
{% endtabs %}



## page\_view and purchase

To create touch points 'sites' and  'orders' you can use the following events:

* 'page\_view' to create a touch point 'sites'
* 'purchase' to create a touch point 'orders'
