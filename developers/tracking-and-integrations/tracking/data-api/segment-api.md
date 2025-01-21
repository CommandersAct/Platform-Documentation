# Segment API

## GET segments IDs

Returns the list of segments for the user

#### Resource URL <a href="#resource-url" id="resource-url"></a>

https://api.commander1.com/api/dms/segmentation/segments

#### Resource Information <a href="#resource-information" id="resource-information"></a>

| Response formats         | javascript (JSONP)                          |
| ------------------------ | ------------------------------------------- |
| Requires authentication? | No if tcid is not set, token if tcid is set |

#### Parameters

| NAME             | REQUIREMENT    | EXAMPLE VALUES                   | DESCRIPTION                           |
| ---------------- | -------------- | -------------------------------- | ------------------------------------- |
| site             | \d+            | 1234                             | Id of the site to query detail for    |
| tcid (optional)  | \d+            | 1234                             | Id of the tcid (if cookie is disable) |
| token (optional) | \[a-zA-Z0-9]\* | WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA | Security token (if tcid is set)       |
| callback         | \w+            | do\_something                    | javascript callback method for JSONP  |

#### Example Request <a href="#example-request" id="example-request"></a>

`GET`

https://api.commander1.com/api/dms/segmentation/segments?site=1234\&callback=tC\_funcEngage

#### Example Result <a href="#example-result" id="example-result"></a>

```
/**/tC_funcEngage(["F92C4F26"]);
```

## GET segments list

Returns the list of segments created in Engage UIX

#### Resource URL <a href="#resource-url" id="resource-url"></a>

https://api.commander1.com/api/dms/segmentation/segments/list

#### Resource Information <a href="#resource-information" id="resource-information"></a>

| Response formats         | JSON        |
| ------------------------ | ----------- |
| Requires authentication? | Yes (token) |

#### Parameters

| NAME  | REQUIREMENT    | EXAMPLE VALUES                   | DESCRIPTION                        |
| ----- | -------------- | -------------------------------- | ---------------------------------- |
| site  | d+             | 1234                             | Id of the site to query detail for |
| token | \[a-zA-Z0-9]\* | WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA | Security token                     |

#### Example Request <a href="#example-request" id="example-request"></a>

`GET`

https://api.commander1.com/api/dms/segmentation/segments/list?site=1234\&token=WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA

#### Example Result <a href="#example-result" id="example-result"></a>

```
[{"id":"BBFAC450","label":"VIP prospect"},{"id":"3DCC6A0A","label":"New customer"}]
```

