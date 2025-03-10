# Video events

Commanders Act's video specification lets you define how a customer engages with your videos and the related ad content.

This documentation details the conventions and best practices for sending events when tracking videos. The document clarifies the structure and classification of these events, which fall into four categories: `Playback`, `Content`, `Ads` and `Video Settings`.

## Playback

Playback events are tied to the actual playback of video content and track information about the video player.

For example, when a customer plays a video on an app, a Video Playback Started event is sent along with a unique session\_id. All subsequent events generated from that session are tied to the same session\_id.

If a web page has two video players, there will be two separate sessions and associated session\_ids. However, if two separate videos are played on the same video player, they will still be considered a single session with two associated pieces of content.

## Playback Events Properties

All the playback events share the same properties that describe the current state of the video player.

The following table lists all the properties of this playback event object in detail:

<table><thead><tr><th width="250">Property</th><th width="120">Type</th><th width="101">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>video_session_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</td></tr><tr><td><code>video_title</code></td><td><code>String</code></td><td>No</td><td>Denotes the title of the video content.</td></tr><tr><td><code>video_category</code></td><td><code>String</code></td><td>No</td><td>Denotes the genre of the video content asset.</td></tr><tr><td><code>publisher</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the publisher / creator / author of the</p><p>video content asset.</p></td></tr><tr><td><code>content_asset_id</code></td><td><p><code>String</code> </p><p><code>Array [String]</code></p></td><td><strong>Yes</strong></td><td><p>Content asset ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique asset IDs should be sent. For other</p><p>playback events, a singular content asset ID<br>at the time of the event should be sent.</p></td></tr><tr><td><code>content_pod_id</code></td><td><p><code>String</code> </p><p><code>Array [String]</code></p></td><td>No</td><td><p>Content pod ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique pod IDs should be sent. For other</p><p>playback events, a singular content pod ID<br>associated with the current content pod at the<br>time of the event should be sent.</p></td></tr><tr><td><code>ad_asset_id</code></td><td><p><code>String</code> </p><p><code>Array [String]</code></p></td><td>No</td><td><p>Ad asset ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique ad asset IDs should be sent. For other</p><p>playback events, a singular ad asset ID<br>at the time of the event should be sent.</p></td></tr><tr><td><code>ad_pod_id</code></td><td><p><code>String</code> </p><p><code>Array [String]</code></p></td><td>No</td><td><p>Ad pod ID/s of the video/s playing or</p><p>about to be played.</p><p>For <code>Video Playback Started</code> events, an array</p><p>of unique ad pod IDs should be sent. For other</p><p>playback events, a singular content pod ID<br>associated with the current ad pod at the<br>time of the event should be sent.</p></td></tr><tr><td><code>ad_type</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the type of ad playing at the time of the</p><p>event. The values can be '<code>pre-roll</code>', ' <code>mid-roll</code>', or</p><p>'<code>post-roll</code>'.</p></td></tr><tr><td><code>cursor_position</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td>Denotes the current index position of the playhead<br>in seconds. It includes the duration of any seen ads.<br><br>Not required in <code>video_buffer_start</code> and <code>video_buffer_complete</code> events<br><br>If the playback is a livestream, refer to the<br>documentation of the relevant destination for steps<br>on correctly passing the playhead position.</td></tr><tr><td><code>seek_position</code></td><td><code>Integer</code></td><td>No</td><td><p>Denotes the index position of the playhead where the</p><p>user is seeking to.</p><p>Only applicable on the <code>video_seek_start</code> and <code>video_seek_complete</code><br>events. On <code>video_seek_complete</code> events,</p><p>the <code>seek_position</code> should be equal to <code>cursor_position</code>.</p></td></tr><tr><td><code>total_length</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>Denotes the total duration of the video playback</p><p>in seconds. Includes the whole duration of all</p><p>the content and ads included in the session.</p><p>Set to <code>null</code> in case of a livestream playback.</p></td></tr><tr><td><code>bitrate</code></td><td><code>Integer</code></td><td>No</td><td>Bit rate of the video playback, denoted in <code>kbps</code></td></tr><tr><td><code>framerate</code></td><td><code>Float</code></td><td>No</td><td>Denotes the average frame rate of the video<br>playback in <code>fps</code>.</td></tr><tr><td><code>video_player</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the name of the video player used for</p><p>playback. Example: <code>youtube</code>, <code>vimeo</code>, etc.</p></td></tr><tr><td><code>sound</code></td><td><code>Integer</code></td><td>No</td><td><p>Denotes the sound level of the video playback.</p><p>Range is from 0-100, where 0 represents mute</p><p>and 100 is full volume.</p></td></tr><tr><td><code>full_screen</code></td><td><code>Boolean</code></td><td>No</td><td>Set to <code>true</code> if the playback is in fullscreen<br>mode.</td></tr><tr><td><code>ad_enabled</code></td><td><code>Boolean</code></td><td>No</td><td><p>Set to <code>false</code> if the user has any ad blockers.</p><p><br>If the user can view your video ads, it is set to</p><p><code>true</code>.</p></td></tr><tr><td><code>image_quality</code></td><td><code>String</code></td><td>No</td><td>Specifies the quality of the video.<br><br>Examples: 'hd1080', 'highres'</td></tr><tr><td><code>interruption_method</code></td><td><code>String</code></td><td>No</td><td><p>For the <code>Video Playback Interrupted</code> events,<br>you can send this property denoting how the</p><p>playback was interrupted.</p><p>Some examples include 'device_lock', 'call', and</p><p>'browser_redirect'.</p></td></tr><tr><td><code>livestream</code></td><td><code>Boolean</code></td><td>No</td><td>Set to <code>true</code> in case the playback is a live stream,<br>else set to <code>false</code>.</td></tr></tbody></table>

## Playback Events

This section details all the video playback events.

For more information on each of the properties associated with these events, refer to the **Playback Event Properties** section.

### Video Playback Started

This event is associated with the user action of pressing the play button on the video player to initiate the video playback.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_start, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_start, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_start, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Paused

This event corresponds to the user action of pausing the video playback.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_pause, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_pause, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_pause andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_pause, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Interrupted

This event is sent when the video playback stops unintentionally. Network loss, user closing the browser, redirect, etc. are some of the common reasons. You can pass the cause within the property `interruption_method`.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
    "interruption_method":"network_loss"
}
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_error, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_error, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_error andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_error, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Buffer Started

This corresponds to the event of buffering content or an advertisement.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_buffer_start, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_buffer_start, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_buffer_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_buffer_start, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Buffer Completed

This corresponds to the event when the playback finishes buffering the content or an advertisement.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_buffer_complete, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_buffer_complete, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_buffer_complete andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_buffer_complete, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Seek Started

This event is sent when a user manually seeks a certain cursor position of the video content or an advertisement in the playback. The `cursor_position` property indicates where the user is seeking from (time in seconds) and the `seek_position` indicates the cursor position in the playback where the user is seeking to.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_seek_start, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_seek_start, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_seek_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_seek_start, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Seek Completed

This event is sent after a user manually seeks to a certain cursor position of the video or ad in the playback. The `cursor_position` property indicates where the user resumes the playback.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_seek_complete, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_seek_complete, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_seek_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_seek_complete, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Resumed

This event is sent after the user resumes the video playback after it was paused.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_resume, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_resume, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_resume andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_resume, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Playback Completed

This event is sent after the playback is complete and when the pod session is finished. Note that the `cursor_position` property has the same value as the `total_length` property.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val playbackVideoEvent = TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_complete, "YOUR_VIDEO_SESSION_ID")
playbackVideoEvent.contentAssetID = listOf("456", "223")
playbackVideoEvent.cursorPosition = 0
playbackVideoEvent.totalLength = 500
serverSide.execute(playbackVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoPlaybackEvent playbackVideoEvent = new TCVideoPlaybackEvent(ETCVideoPlaybackMode.video_complete, "YOUR_VIDEO_SESSION_ID");
playbackVideoEvent.contentAssetID = Arrays.asList("456", "223");
playbackVideoEvent.cursorPosition = 0;
playbackVideoEvent.totalLength = 500;
serverSide.execute(playbackVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoPlaybackEvent *playbackVideoEvent = [[TCVideoPlaybackEvent alloc] initWithMode: video_resume andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    playbackVideoEvent.contentAssetID =  [@[@"456", @"223"] mutableCopy];
    playbackVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    playbackVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: playbackVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let playbackVideoEvent = TCVideoPlaybackEvent(mode: video_complete, andSessionId: "YOUR_VIDEO_SESSION_ID")
    playbackVideoEvent?.contentAssetID = ["456", "223"]
    playbackVideoEvent?.cursorPosition = 0
    playbackVideoEvent?.totalLength = 500
    serverSide?.execute(playbackVideoEvent)
```
{% endtab %}
{% endtabs %}

## Content

A content **pod** refers to a part / group / segment of the video content or the advertisement within the playback.

Suppose a video playback session has a video and one mid-roll advertisement. This means that the mid-roll ad splits the playback in two separate content pods. The mid-roll ad is included within a single ad pod.

The flow is as follows:

* User starts and completes the first content pod
* User starts and completes the ad
* User starts and completes the second content pod

All of these events within the flow happen within one video playback.

## Content Events Properties

All the content events share the same properties that describe the current state of the video content that is viewed by the user during the playback.

The following table lists all the properties of this playback event object in detail:

<table><thead><tr><th width="226">Property</th><th width="116.33333333333331">Type</th><th width="101">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>video_session_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</td></tr><tr><td><code>content_asset_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>Denotes the unique ID of the video content asset.</td></tr><tr><td><code>content_pod_id</code></td><td><code>String</code></td><td>No</td><td>Denotes the unique ID of the video content pod.</td></tr><tr><td><code>video_title</code></td><td><code>String</code></td><td>No</td><td>Denotes the title of the video content.</td></tr><tr><td><code>video_description</code></td><td><code>String</code></td><td>No</td><td>Describes the video content asset in short.</td></tr><tr><td><code>keywords</code></td><td><code>Array [String]</code></td><td>No</td><td><p>Denotes the relevant keywords associated with the</p><p>categorizing the video content</p></td></tr><tr><td><code>season</code></td><td><code>String</code></td><td>No</td><td>Denotes the season number, if applicable.</td></tr><tr><td><code>episode</code></td><td><code>String</code></td><td>No</td><td>Denotes the episode number, if applicable.</td></tr><tr><td><code>video_category</code></td><td><code>String</code></td><td>No</td><td>Denotes the genre of the video content asset.</td></tr><tr><td><code>program</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the name of the program / show of which</p><p>the video content is a part.</p></td></tr><tr><td><code>publisher</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the publisher / creator / author of the</p><p>video content asset.</p></td></tr><tr><td><code>channel</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the channel in which the video content</p><p>is playing.</p></td></tr><tr><td><code>full_episode</code></td><td><code>Boolean</code></td><td>No</td><td>Set to <code>true</code> the video content asset is a full episode.</td></tr><tr><td><code>livestream</code></td><td>Boolean</td><td>No</td><td><p>If the video content is a live stream, this is set to</p><p><code>true</code>.</p></td></tr><tr><td><code>airdate</code></td><td><p><code>ISO 8601</code></p><p><code>Date String</code></p></td><td>No</td><td><p>Denotes the original date of airing / publishing</p><p>the video content.</p></td></tr><tr><td><code>cursor_position</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>Denotes the current playhead position into the</p><p>video content in seconds. This does not include</p><p>any ads played in this duration.</p><p>In case of live streams, refer to the relevant<br>destination's documentation for details on how to<br>pass this property.</p></td></tr><tr><td><code>total_length</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>The total duration of the video content in</p><p>seconds. This does not include any ads included</p><p>in the playback of this content asset.</p><p>For livestream playback, this should be set to <code>null</code>.</p></td></tr><tr><td><code>bitrate</code></td><td><code>Integer</code></td><td>No</td><td>Denotes the current bit rate in <code>kbps</code>.</td></tr><tr><td><code>framerate</code></td><td><code>Float</code></td><td>No</td><td>Denotes the frame rate in <code>fps</code>.</td></tr></tbody></table>

## Content Events

This section details all the video content events.

For more information on each of the properties associated with these events, refer to the [**Content Events Properties**](video-event-reference.md#content-events-properties) section.

### Video Content Started

This event is sent once the user starts playing video content segment within a playback.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
{
    "event_name": "video_content_start",
    "video_session_id": "98765",
    "content_asset_id": "456",
    "content_pod_id": "XYZ",
    "program": "The Lion King",
    "video_title": "Act 1",
    "video_description": "Invented description",
    "season": "1",
    "episode":"14",
    "channel":"NBC",
    "livestream":false,
    "airdate":"2022-12-20",
    "cursor_position": 5,
    "total_length": 200,
    "video_category": "Animation",
    "publisher": "Disney",
    "full_episode": false,
    "keywords": ["lion", "savannah", "circle of life"],
    "user": {}
}
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val contentVideoEvent = TCVideoContentEvent(ETCVideoContentMode.video_content_start, "YOUR_VIDEO_SESSION_ID")
contentVideoEvent.contentAssetID = "456"
contentVideoEvent.cursorPosition = 0
contentVideoEvent.totalLength = 500
serverSide.execute(contentVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoContentEvent contentVideoEvent = new TCVideoContentEvent(ETCVideoContentMode.video_content_start, "YOUR_VIDEO_SESSION_ID");
contentVideoEvent.contentAssetID = "456";
contentVideoEvent.cursorPosition = 0;
contentVideoEvent.totalLength = 500;
serverSide.execute(contentVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
<pre class="language-objectivec"><code class="lang-objectivec"><strong>    TCVideoContentEvent *addContentEvent = [[TCVideoContentEvent alloc] initWithMode: video_content_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
</strong>    addContentEvent.contentAssetID = @"456";
    addContentEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    addContentEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: addContentEvent];
</code></pre>
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let contentVideoEvent = TCVideoContentEvent(mode: video_content_start, andSessionId: "YOUR_VIDEO_SESSION_ID")
    contentVideoEvent?.contentAssetID = "456"
    contentVideoEvent?.cursorPosition = 0
    contentVideoEvent?.totalLength = 500
    serverSide?.execute(contentVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Content Playing

These events are sent as heartbeats every after a set interval to indicate the length of video viewed by the user, determined by the `cursor_position` property.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
{
    "event_name": "video_content_playing",
    "video_session_id": "56789",
    "content_asset_id": "789",
    "content_pod_id": "ABC",
    "program": "The Jungle Book",
    "video_title": "Act 2",
    "video_description": "Invented description",
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val contentVideoEvent = TCVideoContentEvent(ETCVideoContentMode.video_content_playing, "YOUR_VIDEO_SESSION_ID")
contentVideoEvent.contentAssetID = "456"
contentVideoEvent.cursorPosition = 0
contentVideoEvent.totalLength = 500
serverSide.execute(contentVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoContentEvent contentVideoEvent = new TCVideoContentEvent(ETCVideoContentMode.video_content_playing, "YOUR_VIDEO_SESSION_ID");
contentVideoEvent.contentAssetID = "456";
contentVideoEvent.cursorPosition = 0;
contentVideoEvent.totalLength = 500;
serverSide.execute(contentVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoContentEvent *addContentEvent = [[TCVideoContentEvent alloc] initWithMode: video_content_playing andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addContentEvent.contentAssetID = @"456";
    addContentEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    addContentEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: addContentEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let contentVideoEvent = TCVideoContentEvent(mode: video_content_playing, andSessionId: "YOUR_VIDEO_SESSION_ID")
    contentVideoEvent?.contentAssetID = "456"
    contentVideoEvent?.cursorPosition = 0
    contentVideoEvent?.totalLength = 500
    serverSide?.execute(contentVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Content Quarter Reached

These events are sent when a quarter of the video is reached, determined by the `cursor_position` property.

A sample event is as shown:&#x20;

{% tabs %}
{% tab title="JavaScript" %}
```javascript
{
    "event_name": "video_content_quarter_reached",
    "video_session_id": "56789",
    "content_asset_id": "789",
    "content_pod_id": "ABC",
    "program": "The Jungle Book",
    "video_title": "Act 2",
    "video_description": "Invented description",
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val contentVideoEvent = TCVideoContentEvent(ETCVideoContentMode.video_content_quarter_reached, "YOUR_VIDEO_SESSION_ID")
contentVideoEvent.contentAssetID = "456"
contentVideoEvent.cursorPosition = 0
contentVideoEvent.totalLength = 500
serverSide.execute(contentVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoContentEvent contentVideoEvent = new TCVideoContentEvent(ETCVideoContentMode.video_content_playing, "YOUR_VIDEO_SESSION_ID");
contentVideoEvent.contentAssetID = "456";
contentVideoEvent.cursorPosition = 0;
contentVideoEvent.totalLength = 500;
serverSide.execute(contentVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoContentEvent *addContentEvent = [[TCVideoContentEvent alloc] initWithMode: video_content_quarter_reached andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addContentEvent.contentAssetID = @"456";
    addContentEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    addContentEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: addContentEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let contentVideoEvent = TCVideoContentEvent(mode: video_content_quarter_reached, andSessionId: "YOUR_VIDEO_SESSION_ID")
    contentVideoEvent?.contentAssetID = "456"
    contentVideoEvent?.cursorPosition = 0
    contentVideoEvent?.totalLength = 500
    serverSide?.execute(contentVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Content Completed

This event is sent once the video segment within the playback is completed. Note that the `cursor_position` property has the same value as the `total_length` property.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
{
    "event_name": "video_content_complete",
    "video_session_id": "01234",
    "content_asset_id": "111",
    "content_pod_id": "DEF",
    "program": "Tarzan",
    "video_title": "Finale",
    "video_description": "Invented description",
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val contentVideoEvent = TCVideoContentEvent(ETCVideoContentMode.video_content_complete, "YOUR_VIDEO_SESSION_ID")
contentVideoEvent.contentAssetID = "456"
contentVideoEvent.cursorPosition = 0
contentVideoEvent.totalLength = 500
serverSide.execute(contentVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoContentEvent contentVideoEvent = new TCVideoContentEvent(ETCVideoContentMode.video_content_complete, "YOUR_VIDEO_SESSION_ID");
contentVideoEvent.contentAssetID = "456";
contentVideoEvent.cursorPosition = 0;
contentVideoEvent.totalLength = 500;
serverSide.execute(contentVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoContentEvent *addContentEvent = [[TCVideoContentEvent alloc] initWithMode: video_content_complete andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addContentEvent.contentAssetID = @"456";
    addContentEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 0];
    addContentEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 500];;
    [serverside execute: addContentEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let contentVideoEvent = TCVideoContentEvent(mode: video_content_complete, andSessionId: "YOUR_VIDEO_SESSION_ID")
    contentVideoEvent?.contentAssetID = "456"
    contentVideoEvent?.cursorPosition = 0
    contentVideoEvent?.totalLength = 500
    serverSide?.execute(contentVideoEvent)
```
{% endtab %}
{% endtabs %}

## Ads

## Ad Events Properties

All the ad events share the same properties that describe the current state of the video ad content that a user is interacting with during the playback.

The following table lists all the properties of this ad event object in detail:

<table><thead><tr><th width="211">Property</th><th width="113.33333333333331">Type</th><th width="111">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>video_session_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</td></tr><tr><td><code>ad_asset_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>Denotes the unique ID of the ad asset.</td></tr><tr><td><code>ad_pod_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>Denotes the unique ID of the ad pod.</td></tr><tr><td><code>pod_position</code></td><td><code>Integer</code></td><td>No</td><td><p>Denotes the position of the ad asset relative</p><p>to other ads in the same pod.</p></td></tr><tr><td><code>ad_type</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the type of ad playing at the time of the</p><p>event. The values can be '<code>pre-roll</code>', ' <code>mid-roll</code>', or</p><p>'<code>post-roll</code>'.</p></td></tr><tr><td><code>pod_length</code></td><td><code>Integer</code></td><td>No</td><td><p>Denotes the number of ad assets in the current</p><p>ad pod.</p></td></tr><tr><td><code>video_title</code></td><td><code>String</code></td><td>No</td><td>Denotes the title of the ad.</td></tr><tr><td><code>publisher</code></td><td><code>String</code></td><td>No</td><td>Denotes the author/ creator/ publisher of the ad.</td></tr><tr><td><code>cursor_position</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>The current playhead position in relation to the</p><p>total length of the ad, in seconds.</p></td></tr><tr><td><code>total_length</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td>Denotes the total length of the ad asset in seconds.</td></tr><tr><td><code>load_type</code></td><td><code>Enum</code></td><td>No</td><td><p>Denotes if the ads are loaded dynamically or if</p><p>they are the same for all the users.<br><br>Values can be either '<code>dynamic</code>' or ' <code>linear</code> '.</p></td></tr><tr><td><code>ad_quartile</code></td><td><code>Integer</code></td><td>No</td><td><p>For the <code>Video Ad Playing</code> event, this property</p><p>can be used to indicate when a specific ad quartile</p><p>is reached.</p><p>If you are using a client-side library to track your</p><p>video events, this property is optional as Commanders Act</p><p>automatically tracks the ad quartiles.</p></td></tr></tbody></table>

## Ad Events

This section details all the ad events.

For more information on each of the properties associated with these events, refer to the **Ad Event Properties** section.

### Video Ad Started

This event is sent when an advertisement roll starts playing within the video playback.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_start, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_start, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_start, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Playing

This event is sent between set intervals when the video ad is playing and is determined by the `cursor_position` property.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_playing, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_playing, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_playing andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_playing, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Stop

This event is sent after the user has viewed a video ad completely. Note that the `cursor_position` property has the same value as the `total_length` property.

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_stop, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_stop, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_stop andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_playing, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Completed

This event is sent after the user has viewed the video ad roll completely. Note that the `cursor_position` property has the same value as the `total_length` property.

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_complete, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_complete, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_complete andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_complete, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Skip

This event is sent when the user click on the skip ad button.&#x20;

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_skip, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_skip, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_skip andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_skip, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Break Started

This event is sent when an advertisement break starts playing while the video playback.

A sample event is as shown:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_break_start, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_break_start, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_break_start andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_break_start, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Break Completed

This event is sent after the user has viewed the video ad break pod completely. Note that the `cursor_position` property has the same value as the `total_length` property.

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_break_complete, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_break_complete, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_break_complete andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_break_complete, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Ad Click

This event is sent when the user click on the add.&#x20;

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val addVideoEvent = TCVideoAdEvent(ETCVideoAdMode.video_ad_click, "YOUR_VIDEO_SESSION_ID")
addVideoEvent.adAssetID = "456"
addVideoEvent.adPodID = "839"
addVideoEvent.cursorPosition = 12
addVideoEvent.totalLength = 211
serverSide.execute(addVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoAdEvent addVideoEvent = new TCVideoAdEvent(ETCVideoAdMode.video_ad_click, "YOUR_VIDEO_SESSION_ID");
addVideoEvent.adAssetID = "456";
addVideoEvent.adPodID = "839";
addVideoEvent.cursorPosition = 12;
addVideoEvent.totalLength = 211;
serverSide.execute(addVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoAdEvent *addVideoEvent = [[TCVideoAdEvent alloc] initWithMode: video_ad_click andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    addVideoEvent.adAssetID = @"456";
    addVideoEvent.adPodID = @"839";
    addVideoEvent.cursorPosition = [[NSDecimalNumber alloc] initWithInt: 12];
    addVideoEvent.totalLength = [[NSDecimalNumber alloc] initWithInt: 211];
    [serverside execute: addVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let addVideoEvent = TCVideoAdEvent(mode: video_ad_click, andSessionId: "YOUR_VIDEO_SESSION_ID")
    addVideoEvent?.adAssetID = "456"
    addVideoEvent?.adPodID = "839"
    addVideoEvent?.cursorPosition = 12
    addVideoEvent?.totalLength = 211
    serverSide?.execute(addVideoEvent)
```
{% endtab %}
{% endtabs %}

## Settings

## Setting Events Properties

All the settings events share the same properties that describe the current state of the video  content that a user is interacting with during the playback.

<table><thead><tr><th width="220">Property</th><th width="152.33333333333331">Type</th><th width="128">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>video_session_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>A unique ID that ties all the events<br>generated from a specific playback session.<br><br>These events include playback, content, and<br>ad events.</td></tr><tr><td><code>content_asset_id</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>Denotes the unique ID of the video content asset.</td></tr><tr><td><code>content_pod_id</code></td><td><code>String</code></td><td>No</td><td>Denotes the unique ID of the video content pod.</td></tr><tr><td><code>ad_asset_id</code></td><td><code>String</code></td><td>No</td><td>Denotes the unique ID of the ad asset.</td></tr><tr><td><code>ad_pod_id</code></td><td><code>String</code></td><td>No</td><td>Denotes the unique ID of the ad pod.</td></tr><tr><td><code>ad_type</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the type of ad playing at the time of the</p><p>event. The values can be '<code>pre-roll</code>', ' <code>mid-roll</code>', or</p><p>'<code>post-roll</code>'.</p></td></tr><tr><td><code>video_title</code></td><td><code>String</code></td><td>No</td><td>Denotes the title of the video content.</td></tr><tr><td><code>video_description</code></td><td><code>String</code></td><td>No</td><td>Describes the video content asset in short.</td></tr><tr><td><code>keywords</code></td><td><code>Array [String]</code></td><td>No</td><td><p>Denotes the relevant keywords associated with the</p><p>categorizing the video content</p></td></tr><tr><td><code>season</code></td><td><code>String</code></td><td>No</td><td>Denotes the season number, if applicable.</td></tr><tr><td><code>episode</code></td><td><code>String</code></td><td>No</td><td>Denotes the episode number, if applicable.</td></tr><tr><td><code>video_category</code></td><td><code>String</code></td><td>No</td><td>Denotes the genre of the video content asset.</td></tr><tr><td><code>program</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the name of the program / show of which</p><p>the video content is a part.</p></td></tr><tr><td><code>publisher</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the publisher / creator / author of the</p><p>video content asset.</p></td></tr><tr><td><code>channel</code></td><td><code>String</code></td><td>No</td><td><p>Denotes the channel in which the video content</p><p>is playing.</p></td></tr><tr><td><code>full_episode</code></td><td><code>Boolean</code></td><td>No</td><td>Set to <code>true</code> the video content asset is a full episode.</td></tr><tr><td><code>livestream</code></td><td><code>Boolean</code></td><td>No</td><td><p>If the video content is a live stream, this is set to</p><p><code>true</code>.</p></td></tr><tr><td><code>airdate</code></td><td><p><code>ISO 8601</code></p><p><code>Date String</code></p></td><td>No</td><td><p>Denotes the original date of airing / publishing</p><p>the video content.</p></td></tr><tr><td><code>cursor_position</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>Denotes the current playhead position into the</p><p>video content in seconds. This does not include</p><p>any ads played in this duration.</p><p>In case of live streams, refer to the relevant<br>destination's documentation for details on how to<br>pass this property.</p></td></tr><tr><td><code>total_length</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>The total duration of the video content in</p><p>seconds. This does not include any ads included</p><p>in the playback of this content asset.</p><p>For livestream playback, this should be set to <code>null</code>.</p></td></tr><tr><td><code>bitrate</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td>Denotes the current bit rate in <code>kbps</code>.</td></tr><tr><td><code>framerate</code></td><td><code>Float</code></td><td>No</td><td>Denotes the frame rate in <code>fps</code>.</td></tr><tr><td><code>sound</code></td><td><code>Integer</code></td><td><strong>Yes</strong></td><td><p>Denotes the current video sound level</p><p>Required in <code>video_volume</code> event</p></td></tr><tr><td><code>full_screen</code></td><td><code>Boolean</code></td><td><strong>Yes</strong></td><td>Denotes the current video screen mode.<br>Required in <code>video_fullscreen_on</code> and <code>video_full_screen_off</code> events</td></tr><tr><td><code>ad_enabled</code></td><td><code>Boolean</code></td><td>No</td><td>Denotes if ad were enabled</td></tr><tr><td><code>image_quality</code></td><td><code>String</code></td><td><strong>Yes</strong></td><td>Denotes the current video queity resolution.<br>Required in <code>video_quality</code> event</td></tr></tbody></table>



## Resuming Playback

## Setting Events

This section details all the video settings events.

For more information on each of the properties associated with these events, refer to the [**Settings Event Properties**](video-event-reference.md#video-settings-properties) section.

### Video Volume

This event is sent when the user modify the audio volume of the video player.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_volume, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_volume, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_volume andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_volume, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Speed

This event is sent when the user modify the speed of the video player.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_speed, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_speed, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_speed andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_speed, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Subtitle On

This event is sent when the user turns on the subtitles of the video player.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_subtitle_on, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_subtitle_on, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_subtitle_on andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_subtitle_on, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Subtitle Off

This event is sent when the user turns off the subtitles of the video player.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_subtitle_off, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_subtitle_off, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_subtitle_off andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_subtitle_off, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video FullScreen On

This event is sent when the user turns on the full screen view of the video player.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_fullscreen_on, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_fullscreen_on, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_fullscreen_on andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_fullscreen_on, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Full Screen Off

This event is sent when the user turns off the full screen view of the video player.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_fullscreen_off, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_fullscreen_off, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_fullscreen_off andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_fullscreen_on, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}

### Video Quality

This event is sent when the video quality of the video player is modified.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_quality, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_quality, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_quality andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_quality, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}



### Video Share

This event is sent when the video is shared by the user.

A sample event is as shown below:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
{
    "event_name": "video_share",
    "user": {},
    "video_session_id": "98765",
    "content_asset_id": ["0133370", "123456"],
    "content_pod_id": ["CAA", "CAB", "CAD"],
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
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val settingVideoEvent = TCVideoSettingEvent(ETCVideoSettingMode.video_share, "YOUR_VIDEO_SESSION_ID")
settingVideoEvent.contentAssetID = "456"
settingVideoEvent.imageQuality = "720"
serverSide.execute(settingVideoEvent)
```
{% endtab %}

{% tab title="Java (Android)" %}
```java
TCVideoSettingEvent settingVideoEvent = new TCVideoSettingEvent(ETCVideoSettingMode.video_share, "YOUR_VIDEO_SESSION_ID");
settingVideoEvent.contentAssetID = "456";
settingVideoEvent.imageQuality = "720";
serverSide.execute(settingVideoEvent);
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
    TCVideoSettingEvent *settingVideoEvent = [[TCVideoSettingEvent alloc] initWithMode: video_share andSessionId: @"YOUR_VIDEO_SESSION_ID"];
    settingVideoEvent.contentAssetID = @"456";
    settingVideoEvent.imageQuality =  @"720";
    [serverside execute: settingVideoEvent];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let settingVideoEvent = TCVideoSettingEvent(mode: video_share, andSessionId: "YOUR_VIDEO_SESSION_ID")
    settingVideoEvent?.contentAssetID = "456"
    settingVideoEvent?.imageQuality = "720"
    serverSide?.execute(settingVideoEvent)
```
{% endtab %}
{% endtabs %}



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
  content_asset_id: "123",
  content_pod_id: "CAA",
  video_title: "Raw is War!!",
  video_description: "Sample description",
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
  content_asset_id: "123",
  content_pod_id: "CAA",
  video_title: "Raw is War!!",
  video_description: "Sample description",
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
  ad_asset_id: "ad1",
  ad_pod_id: "adCAA",
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
  ad_asset_id: "ad1",
  ad_pod_id: "adCAA",
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
  ad_asset_id: "ad1",
  ad_pod_id: "adCAA",
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
  content_asset_id: "123",
  content_pod_id: "CAA",
  video_title: "Raw is War!!",
  video_description: "Sample description",
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
  content_asset_id: "123",
  content_pod_id: "CAA",
  video_title: "Raw is War!!",
  video_description: "Sample description",
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
  video_session_id: "12345",
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
