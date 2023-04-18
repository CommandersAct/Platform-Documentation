# Web container setup

A web container is a JavaScript file which has two purposes:

·       To be able to use native functions & methods of the TMS

·       To execute the partners solutions (tags) contained inside

&#x20;

It is possible, as it is often the case, to have several containers for the same site or even the same page.

The URL of each JavaScript Web Container file will be provided alongside the Container IDs and Container Names by a Commanders Act Consultant during the setup process.

### Implementation of the containers on the page

Web container are usually installed by implementing a `<script>` html node on every page of your website that holds a `src` attribute that points to the Container URL.&#x20;

The containers can be placed in different locations in the page source’s code depending on their use and your type of business.

&#x20;

Here’s a common example with 3 containers:     &#x20;

| A/B-test (optional) | In the \<head>              |
| ------------------- | --------------------------- |
| Analytics           | At the beginning of \<body> |
| Marketing           | At the end of \</body >     |

&#x20;

\<head> container's location is usually used for AB test and should be load synchronously, to prevent flickering effect.

We recommended to implement all \<body> containers asynchronously. Simply use the async attribute in the \<script> element.

{% hint style="info" %}
Important : the datalayer must be declared before your containers calls. Otherwise, the tags in the container will not be able to use the variables
{% endhint %}

#### Installation of `<head>` Container

`<head>` Container are used to implement A/B-testing and personalisation Tags that usually impact the visual content of a website before it is presented to the user. Therefore it is important to place them as high as possible in the `<head>` section of your website.

```markup
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <script src="{{ head_container_URL }}"></script>
        (...)
    </head>
    (...)
</html>
```

Please ensure that the `<head>` Container file is loaded synchronously to avoid potential content flickering effects.

#### Installation of `<body>` Container

`<body>` Container are used to implement Tags that measure information. These Containers are therefore placed at the end of the `<body>` section to make sure they have minimal impact on the loading time of the content of the website.

```markup
<!DOCTYPE html>
<html>
    (...)
    <body>
        (...)
        <script src="{{ body_container_URL }}"></script>
    </body>
</html>
```

In contrast to the `<head>` Container it is possible to implement `<body>` Container asynchronously. For example it is possible to load them via JavaScript on the `onload` event of the page or it is possible to use the `async` attribute in the `<script>` element.

### Testing

#### Via Browser Console

It is possible to log all loaded Container files on a site via the JavaScript console of the browser. The JavaScript object `tC.containersLaunched` provides information of each loaded Web Container.&#x20;

Following you will find an example object including its most relevant information:

```javascript
{
    1234: { // TagCommander Account ID
        1: { // ID of the 1st loaded Container
            g: 15,
            v: "5.15" // Version of the 1st loaded Container
        },
        5: { // ID of the 2nd loaded Container
            g: 20,
            v: "55.16" // Version of the 2nd loaded Container
        }
}
```

### Definitions&#x20;

| Metric                 | Description                                                                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Container ID**       | Unique ID of the Container within your account. e.g. 21                                                                                        |
| **Container Name**     | Label for the Container. Can be configured in the Options of TagCommander. e.g. "Header Container"                                             |
| **Container Filename** | Name of the Container JavaScript file, can be configured in the Options of the TagCommander interface. e.g. "tc\_header\_21.js"                |
| **Container URL**      | Complete URL of the Container used for installation. Depends on the hosting method. e.g. "//cdn.tagcommander.com/1234/tc\_footer\_main\_20.js" |
| **Container Version**  | Snapshot of a Container JavaScript file.                                                                                                       |
