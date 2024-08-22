# Datalayer setup

A Commanders Act Data Layer is a JavaScript object that holds metadata of a website as properties to make it available to Tags. In the platform this Data Layer is named "External Variables" to distinguish it from scripted "Internal Variables" that are generated within the Container JavaScript.

### Installation

To install a Commanders Act Data Layer it is necessary to implement a global JavaScript object `tc_vars` that holds the meta data of the page as direct properties. The required Data Layer properties are defined during the Commanders Act setup process, but you can find a list of common properties on [this page](../../web/containers/user-guides-for-browser-side-platform/data-layer-and-data-types/external-variables.md).

{% hint style="info" %}
#### Re-using an Existing Data Layer

In case a website already has a Data Layer installed it is possible to transform it into a Commanders Act Data Layer. Please contact a Commanders Act consultant to implement the transformation.
{% endhint %}

The approach to fill the Data Layer with properties depends on the technology framework that is used on the website and can reach from JavaScript web scraping to templating to hardcoding.

```markup
<script>
    window.tc_vars = {
        env_template: "homepage",
        env_work: "prod",
        page_name: "Homepage",
        page_keywords: ["homepage", "home", "entrypage", "index"],
        product_name: "",
        (…)
    };

    window.tc_vars.user_name = "myuser";
</script>
<script src="{{ container_URL }}"></script>
```

The Data Layer needs to be filled with information before the Web Container file is loaded—otherwise information might not be available at the time the Container JavaScript executes.

{% hint style="warning" %}
#### Race Conditions

Race conditions between the Data Layer properties and the Container JavaScript can be difficult to identify and debug by Commanders Act users. It is therefore important to avoid them during installation!
{% endhint %}

In case multiple Containers are used on the same page it is possible to fill the Data Layer in multiple steps. Global information like the page type should be made available before the first Container is loaded. Information that is only relevant for a certain Container (e.g. product information) can be appended prior to the respective Container.

Following example outlines how a Data Layer can be installed in case both a `<head>` and a `<body>` Container are used on a website.

```markup
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <script>
            window.tc_vars = Object.assign({}, window.tc_vars, {
                env_template: "homepage",
                env_work: "prod"
            });
        </script>
        <script src="{{ head_container_URL }}"></script>
        (…)
    <head>
    <body>
        (…)
        <script>
            window.tc_vars = Object.assign({}, window.tc_vars, {
                page_name: "Homepage",
                page_keywords: ["homepage", "home", "entrypage", "index"]
            });
        </script>
        <script src="{{ body_container_URL }}"></script>
    </body>
</html>
```

{% hint style="info" %}
#### Data Layer Naming Convention

As outlined in the example above the properties of the Data Layer are usually grouped with a prefix notation. E.g. `env_` is used to group environment information and `user_` is used to group user information.

In case a property is not relevant for a certain page (e.g. `product_name` on the privacy policy page) it is recommended to fill it with an empty value (e.g. `""`, `0`, `[]` or `{}`).
{% endhint %}

### Testing

#### Via JavaScript Console

It is possible to investigate the Data Layer in the JavaScript console by logging `tc_vars`.

Following you will find an example output of a `tc_vars` Data Layer in the JavaScript Console.

```javascript
{
    env_template: "homepage",
    env_work: "prod",
    page_name: "Homepage",
    page_keywords: ["homepage", "home", "entrypage", "index"],
    product_name: "",
    (…)
}
```

#### Via Quality Assurance Tag

The Tag template _Commanders Act - Data Layer QA_ in the Commanders Act Tag library automatically outputs Data Layer information to the JavaScript console on each page. This approach has the advantage that it logs a snapshot of the Data Layer at the exact time the Container JavaScript was executed. This allows to identify race conditions between the Data Layer properties and the Container JavaScript to make sure all necessary properties are available in time.
