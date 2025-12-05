# Geoloc API

### Overview

The **Geoloc API** allows you to enrich your website’s traffic data with geographic information about your visitors — **without needing support from your technical team**.\
This service provides precise location attributes such as:

* Continent code
* Country code
* Region
* City
* Postal code
* Latitude & longitude

> **Note:** Geoloc is an **optional, billable feature**. Please contact your **Commanders Act Sales representative** for pricing details.

***

### How It Works

To retrieve geoloc data, our system sends a request to the following endpoint:

```
https://api.commander1.com/geoloc?token=XXX&site=XXX
```

**Parameters:**

| Parameter | Description                                                 |
| --------- | ----------------------------------------------------------- |
| `token`   | API token provided by the Commanders Act support team       |
| `site`    | ID of the site (Commenders Act workspace) requesting geoloc |

The API returns a JSON object containing the visitor’s geographic details.

#### Example Response

```json
{
  "continentCode": "EU",
  "countryCode": "FR",
  "region": "Île-de-France",
  "longitude": 2.3333,
  "latitude": 48.8667,
  "city": "Paris",
  "postalCode": "75001"
}
```

***

### Using Geoloca in your JavaScript custom block

Below is a simple example showing how to call the API and store the result in `tC.internalvars` for use within TMS. You can use this code inside your custom javascript block.

#### Example Script

```javascript
function httpGet(url) {
  var xmlHttp = new XMLHttpRequest();
  xmlHttp.open("GET", url, false); // synchronous request
  xmlHttp.send(null);
  return JSON.parse(xmlHttp.responseText);
}

tC.internalvars.geoloc = httpGet("https://api.commander1.com/geoloc/?site={YOUR SITE ID}&token={YOUR TOKEN}");
```

Once assigned, you can use any field directly via internalvars

```javascript
tC.internalvars.geoloc.continentCode  // "EU"
tC.internalvars.geoloc.countryCode    // "FR"
tC.internalvars.geoloc.region         // "Île-de-France"
tC.internalvars.geoloc.longitude      // 2.3399
tC.internalvars.geoloc.latitude       // 48.8718
tC.internalvars.geoloc.city           // "Paris"
tC.internalvars.geoloc.postalCode     // "75009"
```

These variables can now be used to create your own custom rules, such as display a privacy banner for different countries.
