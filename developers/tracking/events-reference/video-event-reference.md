# Video events reference

Commanders Act's video specification lets you define how a customer engages with your videos and the related ad content.

This documentation details the conventions and best practices for sending events when tracking videos. The document clarifies the structure and classification of these events, which fall into four categories: `Playback`, `Content`, `Ads` and `Video Settings`.

## Playback

Playback events are tied to the actual playback of video content and track information about the video player.

For example, when a customer plays a video on an app, a Video Playback Started event is sent along with a unique session\_id. All subsequent events generated from that session are tied to the same session\_id.

If a web page has two video players, there will be two separate sessions and associated session\_ids. However, if two separate videos are played on the same video player, they will still be considered a single session with two associated pieces of content.

### Playback Events

This section details all the video playback events.

For more information on each of the properties associated with these events, refer to the **Playback Event Properties** section.

#### Video Playback Started

This event is associated with the user action of pressing the play button on the video player to initiate the video playback.

A sample event is as shown below:

```javascript
{
    "event_name": "video_start",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "pre-roll",
    "cursor_position": 0,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Playback Paused

This event corresponds to the user action of pausing the video playback.

A sample event is as shown:

```javascript
{
    "event_name": "video_pause",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0123370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "cursor_position": 10,
    "total_length": 600,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Playback Interrupted

This event is sent when the video playback stops unintentionally. Network loss, user closing the browser, redirect, etc. are some of the common reasons. You can pass the cause within the property `method`.

A sample event is as shown:

```javascript
{
    "event_name": "video_error",
    "user": {},
    "video_session_id": "12345",
    "content_asset_id": ["0144370"],
    "content_pod_id": ["CAA", "CAB"],
    "cursor_position": 0,
    "total_length": 300,
    "bitrate": 128,
    "framerate": 30.00,
    "video_player": "youtube",
    "sound": 68,
    "full_screen": true,
    "ad_enabled": true,
    "image_quality": "hd1080",
    "livestream": false,
    "method":"network loss"
}
```

#### Video Playback Buffer Started

This corresponds to the event of buffering content or an advertisement.

A sample event is as shown:

```javascript
{
    "event_name": "video_buffer_start",
    "user": {},
    "video_session_id": "54321",
    "content_asset_id": ["098765"],
    "content_pod_id": ["CAD", "CAE"],
    "cursor_position": 10,
    "total_length": 600,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Playback Buffer Completed

This corresponds to the event when the playback finishes buffering the content or an advertisement.

A sample event is as shown:

```javascript
{
    "event_name": "video_buffer_complete",
    "user": {},
    "video_session_id": "56789",
    "content_asset_id": ["123456"],
    "content_pod_id": ["CAF", "CAG"],
    "cursor_position": 20,
    "total_length": 400,
    "bitrate": 512,
    "framerate": 60.00,
    "video_player": "dailymotion",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Playback Seek Started

This event is sent when a user manually seeks a certain cursor position of the video content or an advertisement in the playback. The `cursor_position` property indicates where the user is seeking from (time in seconds) and the `seek_position` indicates the cursor position in the playback where the user is seeking to.

A sample event is as shown:

```javascript
{
    "event_name": "video_seek_start",
    "user": {},
    "video_session_id": "abcdef",
    "content_asset_id": ["123456"],
    "content_pod_id": ["XYZ", "XYA"],
    "cursor_position": 59,
    "seek_position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Playback Seek Completed

This event is sent after a user manually seeks to a certain cursor position of the video or ad in the playback. The `cursor_position` property indicates where the user resumes the playback.

A sample event is as shown:

```javascript
{
    "event_name": "video_seek_complete",
    "user": {},
    "video_session_id": "abcdef",
    "content_asset_id": ["123456"],
    "content_pod_id": ["XYZ", "XYA"],
    "cursor_position": 59,
    "seek_position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Playback Resumed

This event is sent after the user resumes the video playback after it was paused.

A sample event is as shown:

```javascript
{
    "event_name": "video_resume",
    "user": {},
    "video_session_id": "abcdef",
    "content_asset_id": ["123456"],
    "content_pod_id": ["XYZ", "XYA"],
    "cursor_position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}


```

#### Video Playback Completed

This event is sent after the playback is complete and when the pod session is finished. Note that the `cursor_position` property has the same value as the `total_length` property.

A sample event is as shown:

```javascript
{
    "event_name": "video_complete",
    "user": {},
    "video_session_id": "abcdef",
    "content_asset_id": ["123456"],
    "content_pod_id": ["XYZ", "XYA"],
    "cursor_position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

### Playback Event Properties

All the playback events share the same properties that describe the current state of the video player.

The following table lists all the properties of this playback event object in detail:

| Property           | Type                                                          | Required | Description                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------ | ------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `video_session_id` | `String`                                                      | **Yes**  | <p>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</p>                                                                                                                                                                                                                        |
| `content_asset_id` | <p><code>String</code> </p><p><code>Array [String]</code></p> | **Yes**  | <p>Content asset ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique asset IDs should be sent. For other</p><p>playback events, a singular content asset ID<br>at the time of the event should be sent.</p>                                                                                    |
| `content_pod_id`   | <p><code>String</code> </p><p><code>Array [String]</code></p> | No       | <p>Content pod ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique pod IDs should be sent. For other</p><p>playback events, a singular content pod ID<br>associated with the current content pod at the<br>time of the event should be sent.</p>                                               |
| `ad_asset_id`      | <p><code>String</code> </p><p><code>Array [String]</code></p> | No       | <p>Ad asset ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique ad asset IDs should be sent. For other</p><p>playback events, a singular ad asset ID<br>at the time of the event should be sent.</p>                                                                                           |
| `ad_pod_id`        | <p><code>String</code> </p><p><code>Array [String]</code></p> | No       | <p>Ad pod ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique ad pod IDs should be sent. For other</p><p>playback events, a singular content pod ID<br>associated with the current ad pod at the<br>time of the event should be sent.</p>                                                      |
| `ad_type`          | `String`                                                      | No       | <p>Denotes the type of ad playing at the time of the</p><p>event. The values can be '<code>pre-roll</code>', ' <code>mid-roll</code>', or</p><p>'<code>post-roll</code>'.</p>                                                                                                                                                                                                      |
| `cursor_position`  | `Integer`                                                     | **Yes**  | <p>Denotes the current index position of the playhead<br>in seconds. It includes the duration of any seen ads.<br><br>Not required in <code>video_buffer_start</code> and <code>video_buffer_complete</code> events<br><br>If the playback is a livestream, refer to the<br>documentation of the relevant destination for steps<br>on correctly passing the playhead position.</p> |
| `seek_position`    | `Integer`                                                     | No       | <p>Denotes the index position of the playhead where the</p><p>user is seeking to.</p><p>Only applicable on the <code>video_seek_start</code> and <code>video_seek_complete</code><br>events. On <code>video_seek_complete</code> events,</p><p>the <code>seek_position</code> should be equal to <code>cursor_position</code>.</p>                                                 |
| `total_length`     | `Integer`                                                     | **Yes**  | <p>Denotes the total duration of the video playback</p><p>in seconds. Includes the whole duration of all</p><p>the content and ads included in the session.</p><p>Set to <code>null</code> in case of a livestream playback.</p>                                                                                                                                                   |
| `bitrate`          | `Integer`                                                     | No       | Bit rate of the video playback, denoted in `kbps`                                                                                                                                                                                                                                                                                                                                  |
| `framerate`        | `Float`                                                       | No       | <p>Denotes the average frame rate of the video<br>playback in <code>fps</code>.</p>                                                                                                                                                                                                                                                                                                |
| `video_player`     | `String`                                                      | No       | <p>Denotes the name of the video player used for</p><p>playback. Example: <code>youtube</code>, <code>vimeo</code>, etc.</p>                                                                                                                                                                                                                                                       |
| `sound`            | `Integer`                                                     | No       | <p>Denotes the sound level of the video playback.</p><p>Range is from 0-100, where 0 represents mute</p><p>and 100 is full volume.</p>                                                                                                                                                                                                                                             |
| `full_screen`      | `Boolean`                                                     | No       | <p>Set to <code>true</code> if the playback is in fullscreen<br>mode.</p>                                                                                                                                                                                                                                                                                                          |
| `ad_enabled`       | `Boolean`                                                     | No       | <p>Set to <code>false</code> if the user has any ad blockers.</p><p><br>If the user can view your video ads, it is set to</p><p><code>true</code>.</p>                                                                                                                                                                                                                             |
| `image_quality`    | `String`                                                      | No       | <p>Specifies the quality of the video.<br><br>Examples: 'hd1080', 'highres'</p>                                                                                                                                                                                                                                                                                                    |
| `method`           | `String`                                                      | No       | <p>For the <code>Video Playback Interrupted</code> events,<br>you can send this property denoting how the</p><p>playback was interrupted.</p><p>Some examples include 'device lock', 'call', and</p><p>'browser redirect'.</p>                                                                                                                                                     |
| `livestream`       | `Boolean`                                                     | No       | <p>Set to <code>true</code> in case the playback is a live stream,<br>else set to <code>false</code>.</p>                                                                                                                                                                                                                                                                          |

## Content

A content **pod** refers to a part / group / segment of the video content or the advertisement within the playback.

Suppose a video playback session has a video and one mid-roll advertisement. This means that the mid-roll ad splits the playback in two separate content pods. The mid-roll ad is included within a single ad pod.

The flow is as follows:

* User starts and completes the first content pod
* User starts and completes the ad
* User starts and completes the second content pod

All of these events within the flow happen within one video playback.

### Content Events

This section details all the video content events.

For more information on each of the properties associated with these events, refer to the **Content Event Properties** section.

#### Video Content Started

This event is sent once the user starts playing video content segment within a playback.

A sample event is as shown:

```javascript
{
    "event_name": "video_content_start",
    "video_session_id": "98765",
    "content_asset_id": "456",
    "content_pod_id": "XYZ",
    "program": "The Lion King",
    "video_title": "Act 1",
    "description": "Invented description",
    "season": "1",
    "episode":"14",
    "channel":"NBC",
    "livestream":flase,
    "airstream":"2022-12-20",
    "cursor_position": 5,
    "total_length": 200,
    "video_category": "Animation",
    "publisher": "Disney",
    "full_episode": false,
    "keywords": ["lion", "savannah", "circle of life"],
    "user": {}
}
```

#### Video Content Playing

These events are sent as heartbeats every after a set interval to indicate the length of video viewed by the user, determined by the `cursor_position` property.

A sample event is as shown:

```javascript
{
    "event_name": "video_content_playing",
    "video_session_id": "56789",
    "content_asset_id": "789",
    "content_pod_id": "ABC",
    "program": "The Jungle Book",
    "video_title": "Act 2",
    "description": "Invented description",
    "season": "2",
    "cursor_position": 123,
    "total_length": 400,
    "video_category": "Adventure",
    "publisher": "Disney",
    "full_episode": false,
    "framerate": 60,
    "bitrate": 4500,
    "keywords": ["jungle", "animals", "mowgli"],
    "user": {}
}
```

#### Video Content Quarter Reached

These events are sent when a quarter of the video is reached, determined by the `cursor_position` property.

A sample event is as shown:&#x20;

```javascript
{
    "event_name": "video_content_quarter_reached",
    "video_session_id": "56789",
    "content_asset_id": "789",
    "content_pod_id": "ABC",
    "program": "The Jungle Book",
    "video_title": "Act 2",
    "description": "Invented description",
    "season": "2",
    "cursor_position": 123,
    "total_length": 400,
    "video_category": "Adventure",
    "publisher": "Disney",
    "full_episode": false,
    "keywords": ["jungle", "animals", "mowgli"],
    "user": {}
}
```

#### Video Content Completed

This event is sent once the video segment within the playback is completed. Note that the `cursor_position` property has the same value as the `total_length` property.

A sample event is as shown:

```javascript
{
    "event_name": "video_content_complete",
    "video_session_id": "01234",
    "content_asset_id": "111",
    "content_pod_id": "DEF",
    "program": "Tarzan",
    "video_title": "Finale",
    "description": "Invented description",
    "season": "4",
    "cursor_position": 300,
    "total_length": 300,
    "video_category": "Adventure",
    "publisher": "Disney",
    "full_episode": true,
    "keywords": ["jungle", "apes", "tarzan"],
    "user": {}
}
```

### Content Event Properties

All the content events share the same properties that describe the current state of the video content that is viewed by the user during the playback.

The following table lists all the properties of this playback event object in detail:

| Property           | Type                                                        | Required | Description                                                                                                                                                                                                                                                                         |
| ------------------ | ----------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `video_session_id` | `String`                                                    | **Yes**  | <p>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</p>                                                                                                                         |
| `content_asset_id` | `String`                                                    | **Yes**  | Denotes the unique ID of the video content asset.                                                                                                                                                                                                                                   |
| `content_pod_id`   | `String`                                                    | No       | Denotes the unique ID of the video content pod.                                                                                                                                                                                                                                     |
| `video_title`      | `String`                                                    | No       | Denotes the title of the video content.                                                                                                                                                                                                                                             |
| `description`      | `String`                                                    | No       | Describes the video content asset in short.                                                                                                                                                                                                                                         |
| `keywords`         | `Array [String]`                                            | No       | <p>Denotes the relevant keywords associated with the</p><p>categorizing the video content</p>                                                                                                                                                                                       |
| `season`           | `String`                                                    | No       | Denotes the season number, if applicable.                                                                                                                                                                                                                                           |
| `episode`          | `String`                                                    | No       | Denotes the episode number, if applicable.                                                                                                                                                                                                                                          |
| `video_category`   | `String`                                                    | No       | Denotes the genre of the video content asset.                                                                                                                                                                                                                                       |
| `program`          | `String`                                                    | No       | <p>Denotes the name of the program / show of which</p><p>the video content is a part.</p>                                                                                                                                                                                           |
| `publisher`        | `String`                                                    | No       | <p>Denotes the publisher / creator / author of the</p><p>video content asset.</p>                                                                                                                                                                                                   |
| `channel`          | `String`                                                    | No       | <p>Denotes the channel in which the video content</p><p>is playing.</p>                                                                                                                                                                                                             |
| `full_episode`     | `Boolean`                                                   | No       | Set to `true` the video content asset is a full episode.                                                                                                                                                                                                                            |
| `livestream`       | Boolean                                                     | No       | <p>If the video content is a live stream, this is set to</p><p><code>true</code>.</p>                                                                                                                                                                                               |
| `airdate`          | <p><code>ISO 8601</code></p><p><code>Date String</code></p> | No       | <p>Denotes the original date of airing / publishing</p><p>the video content.</p>                                                                                                                                                                                                    |
| `cursor_position`  | `Integer`                                                   | **Yes**  | <p>Denotes the current playhead position into the</p><p>video content in seconds. This does not include</p><p>any ads played in this duration.</p><p>In case of live streams, refer to the relevant<br>destination's documentation for details on how to<br>pass this property.</p> |
| `total_length`     | `Integer`                                                   | **Yes**  | <p>The total duration of the video content in</p><p>seconds. This does not include any ads included</p><p>in the playback of this content asset.</p><p>For livestream playback, this should be set to <code>null</code>.</p>                                                        |
| `bitrate`          | `Integer`                                                   | No       | Denotes the current bit rate in `kbps`.                                                                                                                                                                                                                                             |
| `framerate`        | `Float`                                                     | No       | Denotes the frame rate in `fps`.                                                                                                                                                                                                                                                    |

## Ads

### Ad Events

This section details all the ad events.

For more information on each of the properties associated with these events, refer to the **Ad Event Properties** section.

#### Video Ad Started

This event is sent when an advertisement roll starts playing within the video playback.

A sample event is as shown:

```javascript
{
  "event_name": "video_ad_start",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 0,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Playing

This event is sent between set intervals when the video ad is playing and is determined by the `cursor_position` property.

A sample event is as shown:

```javascript
{
  "event_name": "video_ad_playing",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 10,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Stop

This event is sent after the user has viewed a video ad completely. Note that the `cursor_position` property has the same value as the `total_length` property.

```javascript
{
  "event_name": "video_ad_stop",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 30,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Completed

This event is sent after the user has viewed the video ad roll completely. Note that the `cursor_position` property has the same value as the `total_length` property.

```javascript
{
  "event_name": "video_ad_complete",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 30,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Skip

This event is sent when the user click on the skip ad button.&#x20;

```javascript
{
  "event_name": "video_ad_skip",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 20,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Break Started

This event is sent when an advertisement break starts playing while the video playback.

A sample event is as shown:

```javascript
{
  "event_name": "video_ad_break_start",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 0,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Break Completed

This event is sent after the user has viewed the video ad break pod completely. Note that the `cursor_position` property has the same value as the `total_length` property.

```javascript
{
  "event_name": "video_ad_break_complete",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 30,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Click

This event is sent when the user click on the add.&#x20;

```javascript
{
  "event_name": "video_ad_click",
  "user": {},
  "video_session_id": "abcdef",
  "ad_asset_id": "456",
  "ad_pod_id": "XYA",
  "ad_type": "pre-roll",
  "video_title": "SmackDown!",
  "cursor_position": 20,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

### Ad Event Properties

All the ad events share the same properties that describe the current state of the video ad content that a user is interacting with during the playback.

The following table lists all the properties of this playback event object in detail:

| Property           | Type      | Required | Description                                                                                                                                                                                                                                                                                                           |
| ------------------ | --------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `video_session_id` | `String`  | **Yes**  | <p>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</p>                                                                                                                                                           |
| `ad_asset_id`      | `String`  | **Yes**  | Denotes the unique ID of the ad asset.                                                                                                                                                                                                                                                                                |
| `ad_pod_id`        | `String`  | **Yes**  | Denotes the unique ID of the ad pod.                                                                                                                                                                                                                                                                                  |
| `pod_position`     | `Integer` | No       | <p>Denotes the position of the ad asset relative</p><p>to other ads in the same pod.</p>                                                                                                                                                                                                                              |
| `ad_type`          | `String`  | No       | <p>Denotes the type of ad playing at the time of the</p><p>event. The values can be '<code>pre-roll</code>', ' <code>mid-roll</code>', or</p><p>'<code>post-roll</code>'.</p>                                                                                                                                         |
| `pod_length`       | `Integer` | No       | <p>Denotes the number of ad assets in the current</p><p>ad pod.</p>                                                                                                                                                                                                                                                   |
| `video_title`      | `String`  | No       | Denotes the title of the ad.                                                                                                                                                                                                                                                                                          |
| `publisher`        | `String`  | No       | Denotes the author/ creator/ publisher of the ad.                                                                                                                                                                                                                                                                     |
| `cursor_position`  | `Integer` | **Yes**  | <p>The current playhead position in relation to the</p><p>total length of the ad, in seconds.</p>                                                                                                                                                                                                                     |
| `total_length`     | `Integer` | **Yes**  | Denotes the total length of the ad asset in seconds.                                                                                                                                                                                                                                                                  |
| `load_type`        | `Enum`    | No       | <p>Denotes if the ads are loaded dynamically or if</p><p>they are the same for all the users.<br><br>Values can be either '<code>dynamic</code>' or ' <code>linear</code> '.</p>                                                                                                                                      |
| `content`          | `Object`  | No       | <p>Some destinations require the content metadata</p><p>to be sent with the ad events.</p><p>You can send all the metadata as a Content Event<br>Object under this property.</p>                                                                                                                                      |
| `ad_quartile`      | `Integer` | No       | <p>For the <code>Video Ad Playing</code> event, this property</p><p>can be used to indicate when a specific ad quartile</p><p>is reached.</p><p>If you are using a client-side library to track your</p><p>video events, this property is optional as Commanders Act</p><p>automatically tracks the ad quartiles.</p> |

## Settings

### Setting Events

This section details all the video settings events.

For more information on each of the properties associated with these events, refer to the [**Settings Event Properties**](video-event-reference.md#video-settings-properties) section.

#### Video Volume

This event is sent when the user modify the audio volume of the video player.

A sample event is as shown below:

```javascript
{
    "event_name": "video_volume",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "mid-roll",
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Speed

This event is sent when the user modify the speed of the video player.

A sample event is as shown below:

```javascript
{
    "event_name": "video_speed",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "mid-roll",
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Subtitle On

This event is sent when the user turns on the subtitles of the video player.

A sample event is as shown below:

```javascript
{
    "event_name": "video_subtitle_on",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "pre-roll",
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Subtitle Off

This event is sent when the user turns off the subtitles of the video player.

A sample event is as shown below:

```javascript
{
    "event_name": "video_subtitle_off",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "post-roll",
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video FullScreen On

This event is sent when the user turns on the full screen view of the video player.

A sample event is as shown below:

```javascript
{
    "event_name": "video_fullscreen_on",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "post-roll",
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video FullScreen Off

This event is sent when the user turns off the full screen view of the video player.

A sample event is as shown below:

```javascript
{
    "event_name": "video_fullscreen_off",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "pre-roll",
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

#### Video Quality

This event is sent when the video quality of the video player is modified.

A sample event is as shown below:

```javascript
{
    "event_name": "video_quality",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": "mid-roll", 
    "cursor_position": 420,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 120,
    "full_screen": false,
    "ad_enabled": false,
    "image_quality": "hd720",
    "livestream": true
}
```

### Setting Events Properties

All the ad events share the same properties that describe the current state of the video ad content that a user is interacting with during the playback.

| Property           | Type                                                        | Required | Description                                                                                                                                                                                                                                                                         |
| ------------------ | ----------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `video_session_id` | `String`                                                    | **Yes**  | <p>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</p>                                                                                                                         |
| `content_asset_id` | `String`                                                    | **Yes**  | Denotes the unique ID of the video content asset.                                                                                                                                                                                                                                   |
| `content_pod_id`   | `String`                                                    | No       | Denotes the unique ID of the video content pod.                                                                                                                                                                                                                                     |
| `ad_asset_id`      | `String`                                                    | No       | Denotes the unique ID of the ad asset.                                                                                                                                                                                                                                              |
| `ad_pod_id`        | `String`                                                    | No       | Denotes the unique ID of the ad pod.                                                                                                                                                                                                                                                |
| `ad_type`          | `String`                                                    | No       | <p>Denotes the type of ad playing at the time of the</p><p>event. The values can be '<code>pre-roll</code>', ' <code>mid-roll</code>', or</p><p>'<code>post-roll</code>'.</p>                                                                                                       |
| `video_title`      | `String`                                                    | No       | Denotes the title of the video content.                                                                                                                                                                                                                                             |
| `description`      | `String`                                                    | No       | Describes the video content asset in short.                                                                                                                                                                                                                                         |
| `keywords`         | `Array [String]`                                            | No       | <p>Denotes the relevant keywords associated with the</p><p>categorizing the video content</p>                                                                                                                                                                                       |
| `season`           | `String`                                                    | No       | Denotes the season number, if applicable.                                                                                                                                                                                                                                           |
| `episode`          | `String`                                                    | No       | Denotes the episode number, if applicable.                                                                                                                                                                                                                                          |
| `video_category`   | `String`                                                    | No       | Denotes the genre of the video content asset.                                                                                                                                                                                                                                       |
| `program`          | `String`                                                    | No       | <p>Denotes the name of the program / show of which</p><p>the video content is a part.</p>                                                                                                                                                                                           |
| `publisher`        | `String`                                                    | No       | <p>Denotes the publisher / creator / author of the</p><p>video content asset.</p>                                                                                                                                                                                                   |
| `channel`          | `String`                                                    | No       | <p>Denotes the channel in which the video content</p><p>is playing.</p>                                                                                                                                                                                                             |
| `full_episode`     | `Boolean`                                                   | No       | Set to `true` the video content asset is a full episode.                                                                                                                                                                                                                            |
| `livestream`       | `Boolean`                                                   | No       | <p>If the video content is a live stream, this is set to</p><p><code>true</code>.</p>                                                                                                                                                                                               |
| `airdate`          | <p><code>ISO 8601</code></p><p><code>Date String</code></p> | No       | <p>Denotes the original date of airing / publishing</p><p>the video content.</p>                                                                                                                                                                                                    |
| `cursor_position`  | `Integer`                                                   | **Yes**  | <p>Denotes the current playhead position into the</p><p>video content in seconds. This does not include</p><p>any ads played in this duration.</p><p>In case of live streams, refer to the relevant<br>destination's documentation for details on how to<br>pass this property.</p> |
| `total_length`     | `Integer`                                                   | **Yes**  | <p>The total duration of the video content in</p><p>seconds. This does not include any ads included</p><p>in the playback of this content asset.</p><p>For livestream playback, this should be set to <code>null</code>.</p>                                                        |
| `bitrate`          | `Integer`                                                   | **Yes**  | Denotes the current bit rate in `kbps`.                                                                                                                                                                                                                                             |
| `framerate`        | `Float`                                                     | No       | Denotes the frame rate in `fps`.                                                                                                                                                                                                                                                    |
| `sound`            | `Integer`                                                   | **Yes**  | <p>Denotes the current video sound level</p><p>Required in <code>video_volume</code> event</p>                                                                                                                                                                                      |
| `full_screen`      | `Boolean`                                                   | **Yes**  | <p>Denotes the current video screen mode.<br>Required in <code>video_fullscreen_on</code> and <code>video_full_screen_off</code> events</p>                                                                                                                                         |
| `ad_enabled`       | `Boolean`                                                   | No       | Denotes if ad were enabled                                                                                                                                                                                                                                                          |
| `image_quality`    | `String`                                                    | **Yes**  | <p>Denotes the current video queity resolution.<br>Required in <code>video_quality</code> event</p>                                                                                                                                                                                 |



## Resuming Playback

Every `Video Playback Resumed` the event should be followed by an event `Video Content Playing` or a `Video Ad Playing` event, depending on what asset the playback resumes to.

## Video Quality

Commanders Act also lets you track and analyze the performance and quality of your video content during the playback.

Whenever a user changes the video quality during playback, you can track a Video Quality Updated event along with the following properties:

* `bitrate`: Denotes the updated bit rate in `kbps`.
* `framerate`: Denotes the updated frame rate in `fps`.
* `startupTime`: Denotes the time when the video quality was changed by the user.
* `droppedFrames`: Indicates if any frames were dropped during the video quality change.

## Events Lifecycle

The following event flow demonstrates how you can implement the Commanders Act video specification:

#### 1. User presses play on a video player

```javascript
cact("trigger","video_start", {
  video_session_id: "12345",
  content_asset_id: ["123"],
  content_pod_id: ["BAA"],
  ad_asset_id: ["ad1"],
  ad_pod_id: ["adCAA"],
  ad_type: "mid-roll",
  cursor_position: 0,
  total_length: 300,
  bitrate: 128,
  video_player: "youtube",
  sound: 67,
  full_screen: true,
  ad_enabled: false,
  image_quality: "hd1080",
});
```

#### 2. Video playback starts playing the content

```javascript
cact("trigger","video_content_start", {
  video_session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  video_title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  video_category: "entertainment",
  program: "WWE",
  publisher: "WWE",
  cursor_position: 0,
  total_length: 300,
  channel: "ten",
  full_episode: true,
  livestream: false,
  airdate: "2020-04-23",
});
```

#### 3. User views the content for 10 seconds followed by a 10 second heartbeat

```javascript
cact("trigger","video_content_playing", {
  video_session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  video_title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  video_category: "entertainment",
  program: "WWE",
  publisher: "WWE",
  cursor_position: 10,
  total_length: 300,
  channel: "ten",
  full_episode: true,
  livestream: false,
  airdate: "2020-04-23",
})
```

#### 4. Video playback is paused

```javascript
cact("trigger","video_pause", {
  video_session_id: "12345",
  content_asset_id: "123",
  content_pod_id: "CAA",
  ad_asset_id: null,
  ad_pod_id: null,
  ad_type: null,
  cursor_position: 11,
  total_length: 300,
  video_player: "youtube",
  sound: 66,
  bitrate: 128,
  full_screen: true,
  ad_enabled: false,
  image_quality: "hd1080",
});
```

#### 5. User resumes the video playback.

```javascript
cact("trigger","video_resume", {
  video_session_id: "12345",
  content_asset_id: "123",
  content_pod_id: "CAA",
  ad_asset_id: null,
  ad_pod_id: null,
  ad_type: null,
  cursor_position: 11,
  total_length: 300,
  video_player: "youtube",
  sound: 66,
  bitrate: 128,
  full_screen: true,
  ad_enabled: false,
  image_quality: "hd1080",
});
```

#### 6. Ad (mid-roll) starts playing after user resumes playback

```javascript
cact("trigger","video_ad_start", {
  video_session_id: "12345",
  asset_id: "ad1",
  pod_id: "adCAA",
  ad_type: "mid-roll",
  video_title: "Thums Up",
  publisher: "Coca Cola",
  cursor_position: 0,
  total_length: 15,
  load_type: "linear",
});
```

#### 7. User watches the complete 15 second advertisement. Commanders Act also tracks the 10 second heartbeats.

```javascript
cact("trigger","video_ad_playing", {
  video_session_id: "12345",
  asset_id: "ad1",
  pod_id: "adCAA",
  ad_type: "mid-roll",
  video_title: "Thums Up",
  publisher: "Coca Cola",
  cursor_position: 10,
  total_length: 15,
  load_type: "linear",
});
```

#### 8. Video ad plays completely.

```javascript
cact("trigger","video_ad_complete", {
  video_session_id: "12345",
  asset_id: "ad1",
  pod_id: "adCAA",
  ad_type: "mid-roll",
  video_title: "Thums Up",
  publisher: "Coca Cola",
  cursor_position: 15,
  total_length: 15,
  load_type: "linear",
})
```

#### 9. Video content resumes playing. Heartbeats are sent every 10 seconds.

```javascript
cact("trigger","video_content_playing", {
  video_session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  video_title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  video_category: "entertainment",
  program: "WWE",
  publisher: "WWE",
  cursor_position: 11,
  total_length: 300,
  channel: "ten",
  full_episode: true,
  livestream: false,
  airdate: "2020-04-23",
})
```

#### 10. User finishes watching the entire video content.

```javascript
cact("trigger","video_content_complete", {
  video_session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  video_title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  video_category: "entertainment",
  program: "WWE",
  publisher: "WWE",
  cursor_position: 300,
  total_length: 300,
  channel: "ten",
  full_episode: true,
  livestream: false,
  airdate: "2020-04-23",
})
```

#### 11. Video playback finishes.

```javascript
cact("trigger","video_complete", {
  session_id: "12345",
  content_asset_id: null,
  content_pod_id: null,
  ad_asset_id: "ad1",
  ad_pod_id: "adCAA",
  ad_type: null,
  cursor_position: 300,
  total_length: 300,
  sound: 66,
  bitrate: 128,
  full_screen: true,
  video_player: "youtube",
  ad_enabled: false,
  image_quality: "hd1080",
})
```

## FAQ

#### What are pre-roll, mid-roll, and post-roll ads?

* Ads that appear before the start of the video playback are called pre-roll ads.
* Ads that appear in the middle of the playback are mid-roll ads.
* Ads that appear after the video playback are called post-roll ads.

These ads can be a promotional video by the sponsors or a piece of content offered by the content provider.
