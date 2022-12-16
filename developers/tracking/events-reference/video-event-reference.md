# Video event reference

Commanders Act's video specification lets you define how a customer engages with your videos and the related ad content.

This documentation details the conventions and best practices for sending events when tracking videos. The document clarifies the structure and classification of these events, which fall into three categories: `Playback`, `Content`, and `Ads`.

## Playback

Playback events are tied to the actual playback of video content and track information about the video player.

For example, when a customer plays a video on an app, a Video Playback Started event is sent along with a unique session_id. All subsequent events generated from that session are tied to the same session_id.

If a web page has two video players, there will be two separate sessions and associated session_ids.
However, if two separate videos are played on the same video player, they will still be considered a single session with two associated pieces of content.

### Playback Events

This section details all the video playback events.

<div class="infoBlock">
For more information on each of the properties associated with these events, refer to the <strong>Playback Event Properties</strong> section.
</div>

#### Video Playback Started

This event is associated with the user action of pressing the play button on the video player to initiate the video playback.

A sample event is as shown below:

```javascript
{
    "event_name": "video_start",
    "user": {},
    "session_id": "98765",
    "content_asset_ids": ["0133370", "123456"],
    "content_pod_ids": ["CAA", "CAB", "CAD"],
    "ad_asset_id": ["ad1", "ad0", "ad2"],
    "ad_pod_id": ["adCAA", "adCAB", "adCAD"],
    "ad_type": ["mid-roll", "post-roll", "pre-roll"],
    "position": 0,
    "total_length": 600,
    "bitrate": 128,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
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
    "session_id": "98765",
    "content_asset_ids": ["0123370", "123456"],
    "content_pod_ids": ["CAA", "CAB", "CAD"],
    "position": 10,
    "total_length": 600,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
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
    "session_id": "12345",
    "content_asset_ids": ["0144370"],
    "content_pod_ids": ["CAA", "CAB"],
    "position": 0,
    "total_length": 300,
    "bitrate": 128,
    "framerate": 30.00,
    "video_player": "youtube",
    "sound": 68,
    "full_screen": true,
    "ad_enabled": true,
    "quality": "hd1080",
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
    "session_id": "54321",
    "content_asset_ids": ["098765"],
    "content_pod_ids": ["CAD", "CAE"],
    "position": 10,
    "total_length": 600,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
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
    "session_id": "56789",
    "content_asset_ids": ["123456"],
    "content_pod_ids": ["CAF", "CAG"],
    "position": 20,
    "total_length": 400,
    "bitrate": 512,
    "framerate": 60.00,
    "video_player": "dailymotion",
    "sound": 100,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
    "livestream": true
}
```

#### Video Playback Seek Started

This event is sent when a user manually seeks a certain position of the video content or an advertisement in the playback. The `position` property indicates where the user is seeking from \(time in seconds\) and the `seek_position` indicates the position in the playback where the user is seeking to.

A sample event is as shown:

```javascript
{
    "type": "track",
    "event": "Video Playback Seek Started",
    "userId": "user12345",
    "properties": {
      "session_id": "12345",
      "content_asset_ids": ["0144370"],
      "content_pod_ids": ["CAA", "CAB"],
      "position": 47,
      "seek_position": 120,
      "total_length": 300,
      "bitrate": 128,
      "framerate": 30.00,
      "video_player": "youtube",
      "sound": 68,
      "full_screen": true,
      "ad_enabled": true,
      "quality": "hd1080",
      "livestream": false
    }
}
```

#### Video Playback Seek Completed

This event is sent after a user manually seeks to a certain position of the video or ad in the playback. The `position` property indicates where the user resumes the playback.

A sample event is as shown:

```javascript
{
    "event_name": "video_seek_start",
    "user": {},
    "session_id": "abcdef",
    "content_asset_ids": ["123456"],
    "content_pod_ids": ["XYZ", "XYA"],
    "position": 59,
    "seek_position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
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
    "session_id": "abcdef",
    "content_asset_ids": ["123456"],
    "content_pod_ids": ["XYZ", "XYA"],
    "position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
    "livestream": true
}


```

#### Video Playback Completed

This event is sent after the playback is complete and when the session is finished. Note that the `position` property has the same value as the `total_length` property.

A sample event is as shown:

```javascript
{
    "event_name": "video_complete",
    "user": {},
    "session_id": "abcdef",
    "content_asset_ids": ["123456"],
    "content_pod_ids": ["XYZ", "XYA"],
    "position": 150,
    "total_length": 360,
    "bitrate": 256,
    "framerate": 60.00,
    "video_player": "vimeo",
    "sound": 80,
    "full_screen": false,
    "ad_enabled": false,
    "quality": "hd720",
    "livestream": true
}
```

### Playback Event Properties

All the playback events share the same properties that describe the current state of the video player.

The following table lists all the properties of this playback event object in detail:

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <b>Property</b>
      </th>
      <th style="text-align:left">
        <b>Type</b>
      </th>
      <th style="text-align:left">
        <b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">session_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        A unique ID that ties all the events
        <br />
        generated from a specific playback session.
        <br />
        <br />
        These events include playback, content, and
        <br />
        ad events.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>
          <code class="inline-code">content_asset_id</code>
        </p>
        <p>
          <code class="inline-code">content_asset_ids</code>
        </p>
      </td>
      <td style="text-align:left">
        <p>String</p>
        <p>Array [String]</p>
      </td>
      <td style="text-align:left">
        <p>Content asset ID/s of the video/s playing or</p>
        <p>about to be played.</p>
        <p></p>
        <p>
          For <code class="inline-code">Video Playback Started</code> events, an array
        </p>
        <p>of unique asset IDs should be sent. For other</p>
        <p>
          playback events, a singular content asset ID
          <br />
          at the time of the event should be sent.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>
          <code class="inline-code">content_pod_id</code>
        </p>
        <p>
          <code class="inline-code">content_pod_ids</code>
        </p>
      </td>
      <td style="text-align:left">
        <p>String</p>
        <p>Array [String]</p>
      </td>
      <td style="text-align:left">
        <p>Content pod ID/s of the video/s playing or</p>
        <p>about to be played.</p>
        <p></p>
        <p>
          For <code class="inline-code">Video Playback Started</code> events, an array
        </p>
        <p>of unique pod IDs should be sent. For other</p>
        <p>
          playback events, a singular content pod ID
          <br />
          associated with the current content pod at the
          <br />
          time of the event should be sent.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">ad_asset_id</code>
      </td>
      <td style="text-align:left">
        <p>String</p>
        <p>Array [String]</p>
      </td>
      <td style="text-align:left">
        <p>Ad asset ID/s of the video/s playing or</p>
        <p>about to be played.</p>
        <p></p>
        <p>
          For <code class="inline-code">Video Playback Started</code> events, an array
        </p>
        <p>of unique ad asset IDs should be sent. For other</p>
        <p>
          playback events, a singular ad asset ID
          <br />
          at the time of the event should be sent.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">ad_pod_id</code>
      </td>
      <td style="text-align:left">
        <p>String</p>
        <p>Array [String]</p>
      </td>
      <td style="text-align:left">
        <p>Ad pod ID/s of the video/s playing or</p>
        <p>about to be played.</p>
        <p></p>
        <p>
          For <code class="inline-code">Video Playback Started</code> events, an array
        </p>
        <p>of unique ad pod IDs should be sent. For other</p>
        <p>
          playback events, a singular content pod ID
          <br />
          associated with the current ad pod at the
          <br />
          time of the event should be sent.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">ad_type</code>
      </td>
      <td style="text-align:left">Enum</td>
      <td style="text-align:left">
        <p>Denotes the type of ad playing at the time of the</p>
        <p>
          event. The values can be &apos;<code class="inline-code">pre-roll</code>&apos;, &apos;
          <code class="inline-code">mid-roll</code>&apos;, and
        </p>
        <p>
          &apos;<code class="inline-code">post-roll</code>&apos;.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">position</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        Denotes the current index position of the playhead
        <br />
        in seconds. It includes the duration of any seen ads.
        <br />
        <br />
        If the playback is a livestream, refer to the
        <br />
        documentation of the relevant destination for steps
        <br />
        on correctly passing the playhead position.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">seek_position</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>Denotes the index position of the playhead where the</p>
        <p>user is seeking to.</p>
        <p></p>
        <p>
          Only applicable on the <code class="inline-code">Video Playback Seek Started</code>
          <br />
          events. On Video Playback Seek Completed events,
        </p>
        <p>
          the <code class="inline-code">seek_position</code> should be equal to
          <code class="inline-code">position</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">total_length</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>Denotes the total duration of the video playback</p>
        <p>in seconds. Includes the whole duration of all</p>
        <p>the content and ads included in the session.</p>
        <p></p>
        <p>
          Set to <code class="inline-code">null</code> in case of a livestream playback.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">bitrate</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        Bit rate of the video playback, denoted in <code class="inline-code">kbps</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">framerate</code>
      </td>
      <td style="text-align:left">Float</td>
      <td style="text-align:left">
        Denotes the average frame rate of the video
        <br />
        playback in <code class="inline-code">fps</code>.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">video_player</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>Denotes the name of the video player used for</p>
        <p>
          playback. Example: <code class="inline-code">youtube</code>, <code class="inline-code">vimeo</code>, etc.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">sound</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>Denotes the sound level of the video playback.</p>
        <p></p>
        <p>Range is from 0-100, where 0 represents mute</p>
        <p>and 100 is full volume.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">full_screen</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">
        Set to <code class="inline-code">true</code> if the playback is in fullscreen
        <br />
        mode.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">ad_enabled</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">
        <p>
          Set to <code class="inline-code">false</code> if the user has any ad blockers.
        </p>
        <p>
          <br />
          If the user can view your video ads, it is set to
        </p>
        <p>
          <code class="inline-code">true</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">quality</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Specifies the quality of the video.
        <br />
        <br />
        Examples: &apos;hd1080&apos;, &apos;highres&apos;
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">method</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>
          For the <code class="inline-code">Video Playback Interrupted</code> events,
          <br />
          you can send this property denoting how the
        </p>
        <p>playback was interrupted.</p>
        <p></p>
        <p>
          Some examples include &apos;device lock&apos;, &apos;call&apos;, and
        </p>
        <p>&apos;browser redirect&apos;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">livestream</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">
        Set to <code class="inline-code">true</code> in case the playback is a live stream,
        <br />
        else set to <code class="inline-code">false</code>.
      </td>
    </tr>
  </tbody>
</table>

## Content

A content **pod** refers to a part / group / segment of the video content or the advertisement within the playback.

Suppose a video playback session has a video and one mid-roll advertisement. This means that the mid-roll ad splits the playback in two separate content pods. The mid-roll ad is included within a single ad pod.

The flow is as follows:

- User starts and completes the first content pod
- User starts and completes the ad
- User starts and completes the second content pod

<div class="infoBlock">
All of these events within the flow happen within one video playback.
</div>

### Content Events

This section details all the video content events.

<div class="infoBlock">
For more information on each of the properties associated with these events, refer to the <strong>Content Event Properties</strong> section.
</div>

#### Video Content Started

This event is sent once the user starts playing video content segment within a playback.

A sample event is as shown:

```javascript
{
    "event_name": "video_content_start",
    "session_id": "98765",
    "asset_id": "456",
    "pod_id": "XYZ",
    "program": "The Lion King",
    "title": "Act 1",
    "description": "Invented description",
    "season": "1",
    "position": 5,
    "total_length": 200,
    "genre": "Animation",
    "publisher": "Disney",
    "full_episode": false,
    "keywords": ["lion", "savannah", "circle of life"],
    "user": {}
}
```

#### Video Content Playing

These events are sent as heartbeats every after a set interval to indicate the length of video viewed by the user, determined by the `position` property.

A sample event is as shown:

```javascript
{
    "event_name": "video_content_playing",
    "session_id": "56789",
    "asset_id": "789",
    "pod_id": "ABC",
    "program": "The Jungle Book",
    "title": "Act 2",
    "description": "Invented description",
    "season": "2",
    "position": 123,
    "total_length": 400,
    "genre": "Adventure",
    "publisher": "Disney",
    "full_episode": false,
    "keywords": ["jungle", "animals", "mowgli"],
    "user": {}
}
```

#### Video Content Completed

This event is sent once the video segment within the playback is completed. Note that the `position` property has the same value as the `total_length` property.

A sample event is as shown:

```javascript
{
    "event_name": "movie_completed",
    "session_id": "01234",
    "asset_id": "111",
    "pod_id": "DEF",
    "program": "Tarzan",
    "title": "Finale",
    "description": "Invented description",
    "season": "4",
    "position": 300,
    "total_length": 300,
    "genre": "Adventure",
    "publisher": "Disney",
    "full_episode": true,
    "keywords": ["jungle", "apes", "tarzan"],
    "user": {}
}
```

### Content Event Properties

All the content events share the same properties that describe the current state of the video content that is viewed by the user during the playback.

The following table lists all the properties of this playback event object in detail:

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <b>Property</b>
      </th>
      <th style="text-align:left">
        <b>Type</b>
      </th>
      <th style="text-align:left">
        <b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">session_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        A unique ID that ties all the events
        <br />
        generated from a specific playback session.
        <br />
        <br />
        These events include playback, content, and
        <br />
        ad events.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">asset_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Denotes the unique ID of the video content asset.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">pod_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Denotes the unique ID of the video content pod.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">title</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Denotes the title of the video content.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">description</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Describes the video content asset in short.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">keywords</code>
      </td>
      <td style="text-align:left">Array [String]</td>
      <td style="text-align:left">
        <p>Denotes the relevant keywords associated with the</p>
        <p>categorizing the video content</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">season</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Denotes the season number, if applicable.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">episode</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Denotes the episode number, if applicable.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">genre</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Denotes the genre of the video content asset.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">program</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>Denotes the name of the program / show of which</p>
        <p>the video content is a part.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">publisher</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>Denotes the publisher / creator / author of the</p>
        <p>video content asset.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">channel</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>Denotes the channel in which the video content</p>
        <p>is playing.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">full_episode</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">
        Set to <code class="inline-code">true</code> the video content asset is a full episode.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">livestream</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">
        <p>If the video content is a live stream, this is set to</p>
        <p>
          <code class="inline-code">true</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">airdate</code>
      </td>
      <td style="text-align:left">
        <p>ISO 8601</p>
        <p>Date String</p>
      </td>
      <td style="text-align:left">
        <p>Denotes the original date of airing / publishing</p>
        <p>the video content.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">position</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>Denotes the current playhead position into the</p>
        <p>video content in seconds. This does not include</p>
        <p>any ads played in this duration.</p>
        <p></p>
        <p>
          In case of live streams, refer to the relevant
          <br />
          destination&apos;s documentation for details on how to
          <br />
          pass this property.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">total_length</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>The total duration of the video content in</p>
        <p>seconds. This does not include any ads included</p>
        <p>in the playback of this content asset.</p>
        <p></p>
        <p>
          For livestream playback, this should be set to <code class="inline-code">null</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">bitrate</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        Denotes the current bit rate in <code class="inline-code">kbps</code>.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">framerate</code>
      </td>
      <td style="text-align:left">Float</td>
      <td style="text-align:left">
        Denotes the frame rate in <code class="inline-code">fps</code>.
      </td>
    </tr>
  </tbody>
</table>

## Ads

### Ad Events

This section details all the ad events.

<div class="infoBlock">
For more information on each of the properties associated with these events, refer to the <strong>Ad Event Properties</strong> section.
</div>

#### Video Ad Started

This event is sent when an advertisement starts playing within the video playback.

A sample event is as shown:

```javascript
{
  "event_name": "video_ad_start",
  "user": {},
  "session_id": "abcdef",
  "asset_id": "456",
  "pod_id": "XYA",
  "type": "pre-roll",
  "title": "SmackDown!",
  "position": 0,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Playing

This event is sent between set intervals when the video ad is playing and is determined by the `position` property.

A sample event is as shown:

```javascript
{
  "event_name": "video_ad_playing",
  "user": {},
  "session_id": "abcdef",
  "asset_id": "456",
  "pod_id": "XYA",
  "type": "pre-roll",
  "title": "SmackDown!",
  "position": 10,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

#### Video Ad Completed

This event is sent after the user has viewed the video ad completely. Note that the `position` property has the same value as the `total_length` property.

```javascript
{
  "event_name": "video_ad_start",
  "user": {},
  "session_id": "abcdef",
  "asset_id": "456",
  "pod_id": "XYA",
  "type": "pre-roll",
  "title": "SmackDown!",
  "position": 30,
  "total_length": 30,
  "publisher": "WWE",
  "load_type": "linear"
}
```

### Ad Event Properties

All the ad events share the same properties that describe the current state of the video ad content that a user is interacting with during the playback.

The following table lists all the properties of this playback event object in detail:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">session_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        A unique ID that ties all the events
        <br />
        generated from a specific playback session.
        <br />
        <br />
        These events include playback, content, and
        <br />
        ad events.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">asset_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Denotes the unique ID of the ad asset.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">pod_id</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Denotes the unique ID of the ad pod.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">pod_position</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>Denotes the position of the ad asset relative</p>
        <p>to other ads in the same pod.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">pod_length</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>Denotes the number of ad assets in the current</p>
        <p>ad pod.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">type</code>
      </td>
      <td style="text-align:left">Enum</td>
      <td style="text-align:left">
        <p>Denotes the type of ad. Values can be either of</p>
        <p>
          &apos;<code class="inline-code">pre-roll</code>&apos;, &apos;<code class="inline-code">mid-roll</code>&apos;,
          or &apos;<code class="inline-code">post-roll</code>&apos;.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">title</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Denotes the title of the ad.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">publisher</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        Denotes the author/ creator/ publisher of the ad.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">position</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>The current playhead position in relation to the</p>
        <p>total length of the ad, in seconds.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">total_length</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        Denotes the total length of the ad asset in seconds.
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">load_type</code>
      </td>
      <td style="text-align:left">Enum</td>
      <td style="text-align:left">
        <p>Denotes if the ads are loaded dynamically or if</p>
        <p>
          they are the same for all the users.
          <br />
          <br />
          Values can be either &apos;<code class="inline-code">dynamic</code>&apos; or &apos;<code class="inline-code">
            linear
          </code>&apos;.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">content</code>
      </td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>Some destinations require the content metadata</p>
        <p>to be sent with the ad events.</p>
        <p></p>
        <p>
          You can send all the metadata as a Content Event
          <br />
          Object under this property.
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <code class="inline-code">quartile</code>
      </td>
      <td style="text-align:left">Integer</td>
      <td style="text-align:left">
        <p>
          For the <code class="inline-code">Video Ad Playing</code> event, this property
        </p>
        <p>can be used to indicate when a specific ad quartile</p>
        <p>is reached.</p>
        <p></p>
        <p>If you are using a client-side library to track your</p>
        <p>video events, this property is optional as Commanders Act</p>
        <p>automatically tracks the ad quartiles.</p>
      </td>
    </tr>
  </tbody>
</table>

## Resuming Playback

Every `Video Playback Resumed` the event should be followed by a heartbeat event `Video Content Playing` or a `Video Ad Playing` event, depending on what asset the playback resumes to.

## Video Quality

Commanders Act also lets you track and analyze the performance and quality of your video content during the playback.

Whenever a user changes the video quality during playback, you can track a Video Quality Updated event along with the following properties:

- `bitrate`: Denotes the updated bit rate in `kbps`.
- `framerate`: Denotes the updated frame rate in `fps`.
- `startupTime`: Denotes the time when the video quality was changed by the user.
- `droppedFrames`: Indicates if any frames were dropped during the video quality change.

## Events Lifecycle

The following event flow demonstrates how you can implement the Commanders Act video specification:

#### 1. User presses play on a video player

```javascript
cact("trigger","video_start", {
  session_id: "12345",
  content_asset_ids: ["123"],
  content_pod_ids: ["BAA"],
  ad_asset_ids: ["ad1"],
  ad_pod_ids: ["adCAA"],
  ad_types: ["mid-roll"],
  position: 0,
  total_length: 300,
  bitrate: 128,
  video_player: "youtube",
  sound: 67,
  full_screen: true,
  ad_enabled: false,
  quality: "hd1080",
});
```

#### 2. Video playback starts playing the content

```javascript
cact("trigger","video_content_start", {
  session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  genre: "entertainment",
  program: "WWE",
  publisher: "WWE",
  position: 0,
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
  session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  genre: "entertainment",
  program: "WWE",
  publisher: "WWE",
  position: 10,
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
  session_id: "12345",
  content_asset_id: "123",
  content_pod_id: "CAA",
  ad_asset_id: null,
  ad_pod_id: null,
  ad_type: null,
  position: 11,
  total_length: 300,
  video_player: "youtube",
  sound: 66,
  bitrate: 128,
  full_screen: true,
  ad_enabled: false,
  quality: "hd1080",
});
```

#### 5. User resumes the video playback.

```javascript
cact("trigger","video_resume", {
  session_id: "12345",
  content_asset_id: "123",
  content_pod_id: "CAA",
  ad_asset_id: null,
  ad_pod_id: null,
  ad_type: null,
  position: 11,
  total_length: 300,
  video_player: "youtube",
  sound: 66,
  bitrate: 128,
  full_screen: true,
  ad_enabled: false,
  quality: "hd1080",
});
```

#### 6. Ad \(mid-roll\) starts playing after user resumes playback

```javascript
cact("trigger","video_ad_start", {
  session_id: "12345",
  asset_id: "ad1",
  pod_id: "adCAA",
  type: "mid-roll",
  title: "Thums Up",
  publisher: "Coca Cola",
  position: 0,
  total_length: 15,
  load_type: "linear",
});
```

#### 7. User watches the complete 15 second advertisement. Commanders Act also tracks the 10 second heartbeats.

```javascript
cact("trigger","video_ad_playing", {
  session_id: "12345",
  asset_id: "ad1",
  pod_id: "adCAA",
  type: "mid-roll",
  title: "Thums Up",
  publisher: "Coca Cola",
  position: 10,
  total_length: 15,
  load_type: "linear",
});
```

#### 8. Video ad plays completely.

```javascript
cact("trigger","video_ad_complete", {
  session_id: "12345",
  asset_id: "ad1",
  pod_id: "adCAA",
  type: "mid-roll",
  title: "Thums Up",
  publisher: "Coca Cola",
  position: 15,
  total_length: 15,
  load_type: "linear",
})
```

#### 9. Video content resumes playing. Heartbeats are sent every 10 seconds.

```javascript
cact("trigger","video_content_playing", {
  session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  genre: "entertainment",
  program: "WWE",
  publisher: "WWE",
  position: 11,
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
  session_id: "12345",
  asset_id: "123",
  pod_id: "CAA",
  title: "Raw is War!!",
  description: "Sample description",
  keywords: ["wrestling", "entertainment"],
  season: "1",
  episode: "90",
  genre: "entertainment",
  program: "WWE",
  publisher: "WWE",
  position: 300,
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
  position: 300,
  total_length: 300,
  sound: 66,
  bitrate: 128,
  full_screen: true,
  video_player: "youtube",
  ad_enabled: false,
  quality: "hd1080",
})
```

## FAQ

#### What are pre-roll, mid-roll, and post-roll ads?

- Ads that appear before the start of the video playback are called pre-roll ads.
- Ads that appear in the middle of the playback are mid-roll ads.
- Ads that appear after the video playback are called post-roll ads.

These ads can be a promotional video by the sponsors or a piece of content offered by the content provider.
