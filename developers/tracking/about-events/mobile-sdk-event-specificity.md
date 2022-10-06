# Mobile App event specificity

1. [Event SDK mapping](#event-sdk-mapping)
2. [Event specificity for mobile app](##Event specificity for mobile app)
3. [Fields details](##Fields details)
4. [device](###device)
5. [device -> os](###device -> os)
6. [device -> screen](###device -> screen)
7. [device -> network](###device -> network)
8. [device -> Lifecycle](###device -> Lifecycle)
9. [app](###app)

A full event is the addition of event specific information and data gathered by the SDK.
For each event you'll find in the documentation "events reference" all the possible properties and the mandatory ones.

## Event SDK mapping
To create event, you will need to use classes from the SDK which represents the events. As this might be confusing, you'll find here a list of class name and their event counterparts.

All those class names are valid on both Android and iOS.

| event name         | class name              | 
|--------------------|-------------------------|
| any custom event   | TCCustomEvent           |
| add_payment_info   | TCAddPaymentInfoEvent   |
| add_shipping_info  | TCAddShippingInfoEvent  |               
| add_to_cart        | TCAddToCartEvent        |                     
| add_to_wishlist    | TCAddToWishlistEvent    |                 
| begin_checkout     | TCBeginCheckoutEvent    |                 
| generate_lead      | TCGenerateLeadEvent     |                  
| login              | TCLoginEvent            |                         
| page_view          | TCPageViewEvent         |                      
| purchase           | TCPurchaseEvent         |                      
| refund             | TCRefundEvent           |                        
| remove_from_cart   | TCRemoveFromCartEvent   |                
| search             | TCSearchEvent           |                        
| select_content     | TCSelectContentEvent    |                 
| select_item        | TCSelectItemEvent       |                    
| sign_up            | TCSignUpEvent           |                        
| view_cart          | TCViewCartEvent         |                      
| view_item          | TCViewItem              |                           
| view_item_list     | TCViewItemListEvent     |                  

| COMMON SCHEMAS | class name |
|----------------|------------|
| Item           | TCItem     |
| Product        | TCProduct  |
| User           | TCUser     |

| ENUMERATED VALUE | Class name        |
|------------------|-------------------|
| Payment methods  | ETCPaymentMethod  |
| Purchase status  | ETCPurchaseStatus |   

## Event specificity for mobile app

IOS and Android SDK add specific properties regarding the device and app.&#x20; Those are in addition to event managed properties.

{% hint style="info" %}
If you track your mobile applications without using the sdk (with the [http tracking api](../../../features/integrations/sources/sources-catalog/http-tracking-api.md)), you should follow this specification to benefit from plug\&play on destinations\
{% endhint %}

Here are an example of event playload :
```json
{
	"event_name": "search",
	"event_id": "202110130000000000",
	"properties": {
		"search_term": "t-shirts",
		"user": {
			"id": "12345",
			"email": "toto@domain.fr",
			"consent_categories": ["1", "3"]
		}
	},
	"device": {
		"sdk_id": "C32272DB0-C21E-11E4-8DFC-AA07A5B093DB",
		"manufacturer": "Apple",
		"model": "iPhone7.3",
		"name": "maguro",
		"type": "ios",
		"network": {
			"bluetooth": false,
			"carrier": "T-Mobile US",
			"cellular": true,
			"wifi": false
		},
		"os": {
			"name": "iPhone OS",
			"version": "8.1.3"
		},
		"screen": {
			"width": 320,
			"height": 568,
			"density": 2
		},
		"lifecycle": {
			"session_id": "99b0289e-0934-403e-a27c-3585f7ee32f7",
			"new_session": true,
			"session_duration": 40613,
			"current_session": 1427449428069,
			"visit_number": "4",
			"current_visit": 1427449428069,
			"current_version_first_visit": 1427449000000,
			"session_number": "1",
			"first_visit": 1327449000000,
			"last_visit": 1427449000000,
			"last_call": 1427449429999,
			"last_session_start": 1427449000000,
			"last_session_last_hit": 1427449000999,
			"foreground_transitions": 4,
			"foreground_time": 4013,
			"background_time": 121023,
			"first_execute": false,
			"is_first_visit": false
		},
		"timezone": "Europe/Amsterdam"
	},
	"app": {
		"name": "MyApp",
		"version": "58",
		"build": "2.0.755",
		"core_version": "5.0.2",
		"serverside_version": "5.0.1",
		"namespace": "com.production.commandersact"
	},
	"event_timestamp": "1639044446636"
}
```

## Fields details

Here are fields automatically added by the sdk.

(\*) IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**.

### device

| Field name   | Example value                         | Description                                            | Platform |
| ------------ | ------------------------------------- | ------------------------------------------------------ | -------- |
| manufacturer | Apple                                 | The manufacturer of the hardware                       | Both     |
| model        | iPhone7.3                             | The device model                                       | Both     |
| name         | maguro                                | The device given name                                  | Both     |
| sdk\_id      | C32272DB0-C21E-11E4-8DFC-AA07A5B093DB | A random UUID generated at the first launch of the SDK | Both     |
| timezone     | Europe/Paris                          | The detailed timezone                                  | Both     |
| type         | android                               | The os name                                            | Both     |

The next fields require consent and are added when you call "addAdvertisingIDs" from the ServerSide class.

| Field name            | Example value                        | Description                      | Platform |
| --------------------- | ------------------------------------ | -------------------------------- | -------- |
| advertising\_id       | 705EB54D-9FC7-4730-BF1B-A5D0494E1D8C | Either IDFA or AAD               | Both     |
| idfv                  | 5E35A9BA-C945-4A79-80B6-D89139471308 | IDFV                             | iOS      |
| ad\_tracking\_enabled | true                                 | Has the user enabled ad tracking | Both     |


### device -> os

| Field name | Example value | Description               | Platform |
| ---------- | ------------- | ------------------------- | -------- |
| name       | ios           | The operating system name | Both     |
| version    | 15.5          | The OS version            | Both     |

### device -> screen

| Field name | Example value | Description                 | Platform |
| ---------- | ------------- | --------------------------- | -------- |
| width      | 390           | The device’s screen width   | Both     |
| height     | 844           | The device’s screen height  | Both     |
| density    | 2             | The device’s screen density | Android  |

### device -> network

| Field name | Example value | Description                                      | Platform |
| ---------- | ------------- | ------------------------------------------------ | -------- |
| bluetooth  | false         | Is the bluetooth connected                       | Both     |
| cellular   | true          | Is the cellular connected                        | Both     |
| carrier    | T-Mobile US   | Carrier's name (only when cellular is connected) | Android  |
| wifi       | false         | Is the wifi connected                            | Android  |

### device -> Lifecycle

| Field name                     | Example value                        | Description                                                                                                      | Platform |
| ------------------------------ | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- | -------- |
| session\_id                    | F318C0D1-1DDB-4B53-9326-F2078A97CD38 | An id specific to this session                                                                                   | Both     |
| new\_session                   | false                                | True if this hit is the first of a new session                                                                   | Both     |
| session\_duration              | 8291                                 | The time spent during this session                                                                               | Both     |
| current\_session               | 1655824764174                        | Timestamp of the start of the current session                                                                    | Both     |
| visit\_number                  | 1                                    | Number of times the application was launched                                                                     | Both     |
| current\_visit                 | 1655824764174                        | Timestamp of the start of the current visit                                                                      | Both     |
| current\_version\_first\_visit | 1655824764174                        | Timestamp of the first visit for this application version                                                        | Both     |
| session\_number                | 1                                    | The number of sessions                                                                                           | Both     |
| first\_visit                   | 1655824764174                        | Timestamp of the first app visit                                                                                 | Both     |
| last\_visit                    | 1655824764174                        | Timestamp of the last visit                                                                                      | Both     |
| last\_call                     | 1655824772416                        | Timestamp of the previous call                                                                                   | Both     |
| last\_session\_start           | 0                                    | Timestamp of the start of the previous session                                                                   | Both     |
| last\_session\_last\_hit       | 0                                    | Timestamp of the last hit sent during the previous session                                                       | Both     |
| foreground\_transitions        | 2                                    | Number of times the app when from background to foreground                                                       | Both     |
| foreground\_time               | 8278                                 | Time the application spent in foreground                                                                         | Both     |
| background\_time               | 0                                    | Time the application spent in background                                                                         | Both     |
| first\_execute                 | false                                | Is this the first hit of this cold launch                                                                        | Both     |
| is\_first\_visit               | true                                 | Is this the first launch of this application. (together with first execute you can validate a new installations) | Both     |

### app

| Field name          | Example value           | Description                      | Platform |
| ------------------- | ----------------------- | -------------------------------- | -------- |
| namespace           | com.tagcommander.TCDemo | The app name-space               | Both     |
| name                | TCDemo                  | The app name                     | Both     |
| build               | 1                       | The application build ID         | Both     |
| version             | 1.1                     | The app version                  | Both     |
| serverside\_version | 5.1.0                   | The server-side module’s version | Both     |
| core\_version       | 5.1.0                   | The core module’s version        | Both     |
