---
description: Tag Context variables
---

# Tag Context

The Tag Context is a set of variables that are used from within a tag. Please note that the "Container Loaded" trigger does not provide a Tag Context.
If you want to use a Tag Context while having a similar experience than with "Container Loaded", consider using the `container_ready` custom trigger.

## List of variables

### cact_container

Contains various informations about the container. Includes (but not limited to):
* `cact_container.id_container`
* `cact_container.id_site`
* `cact_container.sourceKey`

### cact_event

The event that triggered the Tag. It has a property `cact_event.type` (String) that can be useful to know the type of events that fired the tag.
It will be set to "no_event" by default if no event was provided.

Example:

```javascript
cact('emit', 'page_view', {});
```

From the tag, then `cact_event.type` will have the value 'page_view';

### cact_event_vars

An object that contains all the event variables from the trigger. This is new safer alternative to the old `tc_array_events` object.

#### Example with the emit API:

```javascript
cact('emit', 'page_view', { hello: 'world' });
```
From the tag, then `cact_event_vars` will have the value `{ hello: 'world' }`;

#### Example with the trigger API:

```javascript
cact('trigger', 'page_view', { page_type: 'homepage' });
```
From the tag, then `cact_event_vars` will have the value `{ page_type: 'homepage' }`;

### cact_event_attrs

An object that contains the event attributes. It can be set using the `from` property inside of the `emit` or the `trigger` API.

```html
<a href="/home" onclick="cact('emit', 'page_view', { from: this, hello: 'world' })">Home</a>
```

