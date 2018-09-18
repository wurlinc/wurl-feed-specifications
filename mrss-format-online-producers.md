# MRSS feed formats for Wurl Platform (Online Video Producers)


This page describes the MRSS format a producers of episodic web series should use. In general one feed per series should be created. If you publish multiple video series, provide multiple syndication feeds, one for each video series to be added to the Wurl Index. If your series has seasons we recommend one feed per season. Wurl will transcode your videos to ensure playback on a variety of devices. The format of your videos you provide in the feed need to conform to the [Mezzanine Specification](https://github.com/wurlinc/wurl-feed-specifications/blob/master/recommended-video-formats.md).

For video producers submitting programming for use in Wurl "Streaming Channels", we require one syndication feed for each Show.


Before submitting your feed to Wurl, make sure your feed validates using one of the available validation tools.

#### Elements in `<channel>` section of your syndication feed:

### Title
```xml
<title>Series Title</title>
```
_Required_. Title of your video series. Recommended length 50 characters or less.

### Description
```xml
<description>Series Description</description>
```
_Required_. Brief description of your video series. Recommended length 200 characters or less.

### Image
```xml
<image>
   <url>http://www.myvideosite.com/240X240_logo.png</url>
   <title>New Releases</title>
   <link>http://www.myvideosite.com/vod</link>
</image>
```
_Required_. URL of a thumbnail image (or "cover art") to be associated with your video series or movie. If your video series is a TV series or a movie, cover art aspect ratio should be 3 x 2 with a recommended size of 300 x 444 pixels. For all other video series, cover art should have an aspect ratio of 1:1 (square) with a recommended size of 240 x 240 pixels. We recommended .svg format if image is suitable (when original art is vector format, i.e.: Illustrator). You could also use .jpg or .png format if image is not suitable for .SVG (when original art is bitmap format, i.e.: Photoshop).

### Link
```xml
<link>http://www.myvideosite.com/vod</link>
```
_Required_. URL of your website or app. (Required for feed validation, but not used by Wurl).

### PubDate
```xml
<pubDate>Thu, 10 Sep 2018 12:34:12 -0500</pubDate>
```
_Required_. Date and time of last feed update in RFC-822 date-time format.

### Wurl Series
```xml
<wurl:series>
  <wurl:officialTitle><![CDATA[Game of Thrones]]></wurl:officialTitle>
  <wurl:startYear>2011</wurl:startYear>
  <wurl:season>
     <wurl:seasonNumber>1</wurl:seasonNumber>
     <wurl:seasonTitle>Some title</wurl:seasonTitle>
  </wurl:season>
  <wurl:studio>n/a</wurl:studio>
</wurl:series>
```
_Required if series feed_. Series tag containing series info. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)


#### Your syndication feed should contain multiple `<item>` groups, one for each video. Elements in `<item>` section of feed:


### Title
```xml
<title>A Title</title>
<!-- or -->
<media:title>A Title</media:title>
```
_Required_. Title of the video. Recommended length 50 characters or less.

### Description
```xml
<description>A Description</description>
<!-- or -->
<media:description>A Description</media:description>
```
_Required_. Brief description of your video. Recommended length 200 characters or less.

### PubDate
```xml
<pubDate>Thu, 10 Sep 2018 12:34:12 -0500</pubDate>
```
_Required_. Your video’s release date and time in RFC-822 date-time format.

### Thumbnail
```xml
<media:thumbnail height="720"url="http://www.myvideosite.com/thumbnails/123.jpg" width="1280"/>
```
_Required_. URL of a thumbnail image to be associated with your video. The aspect ratio should be 16:9 and format .jpg, .png, or .svg.

### Content
```xml
<media:content url="http://myvideosite.com/videos/123.mp4" duration="5400"/>
```
_Required_. The URL of a high-quality encoding of your MPEG4 video asset.

### Keywords
```xml
<media:keywords>keyword1, keyword2</media:keywords>
```
_Required_. Highly relevant keywords describing the video. Recommended limit of 10 keywords or phrases. The keywords and phrases should be comma-delimited.

### Guid
```xml
<guid isPermaLink="true">http://www.hbo.com?series_id=123</guid>
```
A string that uniquely identifies the item, typically a URL.

### Genre
```xml
<media:category scheme="urn:wurl:genre">Cooking</media:category>
```
Assigns a genre.

### TMS
```xml
<media:category scheme="urn:wurl:tms:series:id">SH1234</media:category>
<media:category scheme="urn:wurl:tms:episode:id">EP1234</media:category>
```
Assigns a TMS Series or Episode ID.

### IAB Category
```xml
<media:category scheme="urn:iab:categories" label="Video and Computer Games">IAB9-30</media:category>
```
Specify a category for your video using the IAB Content Category taxonomy. The categories are documented in the [IAB’s OPENRTB API Specification Version 2.1](http://www.iab.net/media/file/OpenRTB-API-Specification-Version-2-1.pdf). See the "Web Series MRSS Example" below for a sample or learn more about this by reading the [specification](http://www.iab.net/media/file/OpenRTB-API-Specification-Version-2-1.pdf) or by looking at these [examples](http://dev.twitter.com/mopub/marketplace/iab-categorization)

### Credit
```xml
<media:credit role="actor">Peter Dinklage</media:credit>
<media:credit role="director">Tim Van Patten</media:credit>
<media:credit role="author">David Benioff</media:credit>
```
Notable entity that contributed to the creation of the media object. May include actors, producers, studios, etc. [More...](http://www.rssboard.org/media-rss#media-credit)

### Copyright
```xml
<media:copyright>Wurl 2018</media:copyright>
```
Copyright information for the video. [More...](http://www.rssboard.org/media-rss#media-copyright)

### Wurl Episode
```xml
<wurl:episode>
  <wurl:officialTitle><![CDATA[Winter Is Coming]]></wurl:officialTitle>
  <wurl:seasonNumber>1</wurl:seasonNumber>
  <wurl:episodeNumber>1</wurl:episodeNumber>
  <wurl:firstAired>Sun, 17 Apr 2011 00:00:00 -0000</wurl:firstAired>
</wurl:episode>
```
_Optional_. Episode tag containing additional episode info. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)


#### Web Series MRSS Example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"
                  xmlns:atom="http://www.w3.org/2005/Atom"
                  xmlns:wurl="http://api.wurl.com/wurlrss/1.0">
  <channel>
    <atom:link href="http://mysite.com/rss/my-series.rss" rel="self"
                                                  type="application/rss+xml"/>
    <title>MySite: Gaming Channel</title>
    <description>Latest gaming videos from mysite.com</description>
    <link>http://www.mysite.com</link>
    <image>
      <url>http://mysite.com/thumbnails/series-1.png</url>
      <title>MySite: Gaming Channel</title>
      <link>http://www.mysite.com</link>
    </image>
    <pubDate>Mon, 18 May 2015 18:56:21 +0000</pubDate>
    <media:keywords>kitty, cat, big dog, yarn, fluffy</media:keywords>
    <wurl:series>
      <wurl:officialTitle><![CDATA[Gaming Channel]]></wurl:officialTitle>
      <wurl:startYear>2011</wurl:startYear>
      <wurl:season>
         <wurl:seasonNumber>3</wurl:seasonNumber>
         <wurl:seasonTitle>Point and Shoot</wurl:seasonTitle>
      </wurl:season>
      <wurl:studio>GamingGalore</wurl:studio>
    </wurl:series>
    <item>
      <guid>http://mysite.com/videos/456.mp4</guid>
      <title>Gaming video Y</title>
      <description>A walk-through of the new Y game</description>
      <pubDate>Mon, 18 May 2015 18:56:21 +0000</pubDate>
      <!-- duration in seconds -->
      <media:content url="http://mysite.com/videos/456.mp4" type="video/mp4"
          medium="video" duration="120" lang="en" fileSize="12216320"
          bitrate="128" framerate="25" samplingrate="44.1" channels="2"
          height="200" width="300"/>
      <media:keywords>gaming y</media:keywords>
      <media:thumbnail url="http://mysite.com/thumbnail/video-456.png"
                                                width="320" height="180"/>
      <media:category>gaming</media:category>
      <media:category scheme="urn:iab:categories"
                  label="Video and Computer Games">IAB9-30</media:category>
      <wurl:episode>
        <wurl:officialTitle><![CDATA[Gaming video Y]]></wurl:officialTitle>
        <wurl:seasonNumber>3</wurl:seasonNumber>
        <wurl:episodeNumber>2</wurl:episodeNumber>
        <wurl:firstAired>Sun, 17 Apr 2011 00:00:00 +0000</wurl:firstAired>
      </wurl:episode>
    </item>
    <item>
      <guid>http://mysite.com/videos/123.mp4</guid>
      <title>Gaming video X</title>
      <description>A walk-through of the new X game</description>
      <pubDate>Wed, 1 Apr 2015 18:56:21 +0000</pubDate>
      <!-- duration in seconds -->
      <media:content url="http://mysite.com/videos/123.mp4" type="video/mp4"
          medium="video" duration="120" lang="en" fileSize="12216320"
          bitrate="128" framerate="25" samplingrate="44.1" channels="2"
          height="200" width="300"/>
      <media:keywords>gaming x</media:keywords>
      <media:thumbnail url="http://mysite.com/thumbnail/video-123.png"
                                                width="320" height="180"/>
      <wurl:episode>
        <wurl:officialTitle><![CDATA[Gaming video X]]></wurl:officialTitle>
        <wurl:seasonNumber>3</wurl:seasonNumber>
        <wurl:episodeNumber>1</wurl:episodeNumber>
        <wurl:firstAired>Sat, 16 Apr 2011 00:00:00 +0000</wurl:firstAired>
      </wurl:episode>
    </item>
  </channel>
</rss>

```
