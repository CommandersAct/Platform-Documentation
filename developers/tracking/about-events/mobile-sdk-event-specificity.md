# Mobile SDK event specificity

IOS and Android SDK send specific properties regarding the device and app.\
Here are an example of event playload :&#x20;

```json
{
	"event_name": "search",
	"event_id": "202110130000000000",
	"properties": {
		"search_term": "t-shirts",
		"user": {
			"id": "12345",
			"email": "toto@domain.fr",
			"consent_categories": [1, 3]
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

Here are fields automatically added by sdk and js :

| Automatic FIELD                       | Web container JS or JS SDK | IOS SDK | ANDROID SDK |
| ------------------------------------- | -------------------------- | ------- | ----------- |
| [app.name](http://app.name)           |                            | √       | √           |
| app.version                           |                            | √       | √           |
| app.build                             |                            | √       | √           |
| app.serverside\_version               |                            | √       | √           |
| app.core\_version                     |                            | √       | √           |
| device.type                           |                            |         | √           |
| device.manufacturer                   |                            | √       | √           |
| device.model                          |                            | √       | √           |
| [device.name](http://device.name)     |                            |         | √           |
| [library.name](http://library.name) ? | √                          | √       | √           |
| library.version ?                     | √                          | √       | √           |
| ip\*                                  | √                          | √       | √           |
| locale                                | √                          | √       | √           |
| network.bluetooth                     |                            |         | √           |
| network.carrier                       |                            | √       | √           |
| network.cellular                      |                            | √       | √           |
| network.wifi                          |                            | √       | √           |
| [os.name](http://os.name)             |                            | √       | √           |
| os.version                            |                            | √       | √           |
| properties.path                       | √                          |         |             |
| properties.referrer                   | √                          |         |             |
| properties.title                      | √                          |         |             |
| properties.url                        | √                          |         |             |
| screen.density                        |                            |         | √           |
| screen.height                         |                            | √       | √           |
| screen.width                          |                            | √       | √           |
| userAgent                             | √                          |         | √           |
| timezone                              |                            | √       | √           |

(\*) IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**.

&#x20;

Lifecycle

| Automatic FIELD | **Explanation** | Both platforms? |
| --------------- | --------------- | --------------- |

| Automatic FIELD                | **Explanation**                                                                                                  | Both platforms? |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------- | --------------- |
| session\_id                    | An id specific to this session.                                                                                  | √               |
| new\_session                   | True if this hit is the first of a new session.                                                                  | √               |
| session\_duration              | The time spent during this session.                                                                              | √               |
| current\_session               | Timestamp of the start of the current session.                                                                   | √               |
| visit\_number                  | Number of times the application was launched                                                                     | √               |
| current\_visit                 | Timestamp of the start of the current visit                                                                      | √               |
| current\_version\_first\_visit | Timestamp of the first visit for this application version                                                        | √               |
| session\_number                | The number of sessions                                                                                           | √               |
| first\_visit                   | Timestamp of the first app visit                                                                                 | √               |
| last\_visit                    | Timestamp of the last visit                                                                                      | √               |
| last\_call                     | Timestamp of the previous call                                                                                   | √               |
| last\_session\_start           | Timestamp of the start of the previous session                                                                   | √               |
| last\_session\_last\_hit       | Timestamp of the last hit sent during the previous session                                                       | √               |
| foreground\_transitions        | Number of times the app when from background to foreground                                                       | √               |
| foreground\_time               | Time the application spent in foreground                                                                         | √               |
| background\_time               | Time the application spent in background                                                                         | √               |
| first\_execute                 | Is this the first hit of this launch                                                                             | √               |
| is\_first\_visit               | Is this the first launch of this application. (together with first execute you can validate a new installations) | √               |
