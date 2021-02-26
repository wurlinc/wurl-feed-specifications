# MRSS feed format for Wurl Platform

This page describes the MRSS format video producers are recommended to use in order to on-board their content to the Wurl Platform. We make use of standard RSS/MRSS tags, but in some cases Wurl defined tags will need to be used.

Wurl will transcode your videos to ensure playback on a variety of target platforms. Note that the format of your videos you provide in the feed need to conform to the [Mezzanine Specification](https://github.com/wurlinc/wurl-feed-specifications/blob/master/recommended-video-formats.md).

When on-boarding episodic series data, it is recommended that you provide one feed per Series.
If you publish multiple video series, provide multiple syndication feeds, one for each video series to be added to the Wurl Platform. If your series has multiple seasons we recommend one feed per season.


* [Channel](#channel)
  * [title](#channel-title)
  * [description](#channel-description)
  * [image](#channel-image)
  * [link](#channel-link)
  * [pub-date](#channel-pubdate)
  * [series](#channel-series)
* [Item](#items)
  * [title](#item-title)
  * [description](#item-description)
  * [pub-date](#item-pubdate)
  * [thumbnail](#item-thumbnail)
  * [content](#item-content)
  * [keywords](#item-keywords)
  * [guid](#item-guid)
  * [external-id](#item-external-id)
  * [episode-external-id](#item-episode-external-id)
  * [tms](#item-tms)
  * [genres](#item-genres)
  * [iab](#item-iab)
  * [terms](#item-terms)
  * [closed captions](#item-cc)
  * [ratings](#item-ratings)
  * [episode](#item-episode)
  * [movie](#item-movie)
  * [wurl-tag](#item-tag)
  * [watermark](#item-watermark)
* [Item Undelivered](#itemundelivered)
  * [credit](#item-credit)
  * [copyright](#item-copyright)
  * [price](#item-price)
* [ShortForm Video MRSS Example](#shortform-example)
* [TV Series MRSS Example](#series-example)
* [Movie MRSS Example](#movie-example)

## Channel <a id="channel"></a>
Elements in `<channel>` section of your syndication feed:

### Title <a id="channel-title"></a>
```xml
<title>Series Title</title>
```
_Required_. Title of your video series. Recommended length 50 characters or less.

### Description <a id="channel-description"></a>
```xml
<description>Series Description</description>
```
_Required_. Brief description of your video series. Recommended length 200 characters or less.

### Image <a id="channel-image"></a>
```xml
<image>
   <url>http://www.myvideosite.com/240X240_logo.png</url>
   <title>New Releases</title>
   <link>http://www.myvideosite.com/vod</link>
</image>
```

### Link <a id="channel-link"></a>
```xml
<link>http://www.myvideosite.com/vod</link>
```
_Required_. URL of your website or app. (Required for feed validation, but not used by Wurl).

### PubDate <a id="channel-pubdate"></a>
```xml
<pubDate>Thu, 10 Sep 2018 12:34:12 -0500</pubDate>
```
_Required_. Date and time of last feed update in RFC-822 date-time format.

### Wurl Series <a id="channel-series"></a>
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


## Item <a id="items"></a>
Your syndication feed should contain multiple `<item>` groups, one for each video. Elements in `<item>` section of feed:

### Title <a id="item-title"></a>
```xml
<title>A Title</title>
<!-- or -->
<media:title>A Title</media:title>
```
_Required_. Title of the video. Recommended length 50 characters or less.

### Description <a id="item-description"></a>
```xml
<description>A Description</description>
<!-- or -->
<media:description>A Description</media:description>
```
_Required_. Brief description of your video. Recommended length 200 characters or less.

### PubDate <a id="item-pubdate"></a>
```xml
<pubDate>Thu, 10 Sep 2018 12:34:12 -0500</pubDate>
```
_Required_. Your video’s release date and time in RFC-822 date-time format.

### Thumbnail <a id="item-thumbnail"></a>
```xml
<media:thumbnail height="720"url="http://www.myvideosite.com/thumbnails/123.jpg" width="1280"/>
```
_Required_. URL of a thumbnail image to be associated with your video. The aspect ratio should be 16:9 and format .jpg, .png, or .svg.

### Content <a id="item-content"></a>
```xml
<media:content url="http://myvideosite.com/videos/123.mp4" duration="5400"/>
```
_Required_. The URL of a high-quality encoding of your MPEG4 video asset.

### Keywords <a id="item-keywords"></a>
```xml
<media:keywords>keyword1, keyword2</media:keywords>
```
_Required_. Highly relevant keywords describing the video. Recommended limit of 10 keywords or phrases. The keywords and phrases should be comma-delimited.

### Guid <a id="item-guid"></a>
```xml
<guid isPermaLink="true">http://www.videos.com/item/987654</guid>
```
_Required_. A string that uniquely identifies the item, typically a URL.

### External ID <a id="item-external-id"></a>
```xml
<media:category scheme="urn:wurl:external:id">123456-1</media:category>
```
_Optional_. An external video id used identify the video in a CMS.

### Episode External ID <a id="item-episode-external-id"></a>
```xml
<media:category scheme="urn:wurl:episode_external:id">789-2</media:category>
```
_Optional_. An external id used identify the target Wurl episode.

### TMS <a id="item-tms"></a>
```xml
<media:category scheme="urn:wurl:tms:series:id">SH1234</media:category>
<media:category scheme="urn:wurl:tms:episode:id">EP1234</media:category>
```
_Optional_. Assigns a TMS Series or Episode ID.

### Genres <a id="item-genres"></a>
```xml
<media:category scheme="urn:wurl:genre">Cooking</media:category>
```
_Optional_. Assigns a genre. Video Service specific genres can be added like this:

```xml
<media:category scheme="urn:roku:genre">Action</media:category>
<media:category scheme="urn:roku:genre">Comedy</media:category>
<media:category scheme="urn:samsung:genre">Drama</media:category>
<media:category scheme="urn:samsung:genre">Movies</media:category>
<media:category scheme="urn:sinclair:genre">Suspense</media:category>
<media:category scheme="urn:sinclair:genre">Kids</media:category>
<media:category scheme="urn:nielsen:genre">Devotional</media:category>
<media:category scheme="urn:nielsen:genre">Documentary, General</media:category>
```

### IAB Category <a id="item-iab"></a>
```xml
<media:category scheme="urn:iab:categories" label="Video and Computer Games">IAB9-30</media:category>
```
_Optional_. Specify a category for your video using the IAB Content Category taxonomy. The categories are documented in the [IAB’s OPENRTB API Specification Version 2.1](http://www.iab.net/media/file/OpenRTB-API-Specification-Version-2-1.pdf). See the "Web Series MRSS Example" below for a sample or learn more about this by reading the [specification](http://www.iab.net/media/file/OpenRTB-API-Specification-Version-2-1.pdf)

### Valid <a id="item-terms"></a>
```xml
<dcterms:valid>start=Tue, 02 Dec 2014 00:00:00 -0600;end=Tue, 30 Jun 2015 00:00:00 -0500;scheme=W3C-DTF</dcterms:valid>
```
_Optional_. Start and end date indicating the time period the video is available for viewing. See example below.

### ClosedCaptions <a id="item-cc"></a>
```xml
<wurl:closedCaptions type="SCC" lang="en-us" href="http://wurl.com/en-us.scc"/>
```
_Optional_. Closed captions. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Rating <a id="item-ratings"></a>
```xml
<media:rating scheme="urn:mpaa">pg-13</media:rating>
<media:rating scheme="urn:v-chip">tv-y7-fv</media:rating>
```
_Optional_. This allows content ratings to be declared. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Wurl Episode <a id="item-episode"></a>
```xml
<wurl:episode>
  <wurl:officialTitle><![CDATA[Winter Is Coming]]></wurl:officialTitle>
  <wurl:seasonNumber>1</wurl:seasonNumber>
  <wurl:episodeNumber>1</wurl:episodeNumber>
  <wurl:firstAired>Sun, 17 Apr 2011 00:00:00 -0000</wurl:firstAired>
</wurl:episode>
```
_Required if series feed_. Episode tag containing additional episode meta data. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Wurl Movie <a id="item-episode"></a>
```xml
<wurl:movie>
  <wurl:officialTitle><![CDATA[Jingle All The Way 2]]></wurl:officialTitle>
  <wurl:year>2011</wurl:year>
</wurl:movie>
```
_Required if movie feed_. Movie tag containing series info. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Wurl Tag <a id="item-tag"></a>

```xml
<media:category scheme="urn:wurl:tags">promo</media:category>
<!-- or -->
<media:category scheme="urn:wurl:tags">ad</media:category>
```
_Optional_. This allows you to tag a video as being a promotional video or ad slate.

### Watermark <a id="item-watermark"></a>

```xml
<wurl:watermark>
  <wurl:imageUrl>http://wurl-videos-dev.com/WM/asset/Foo_Logo.png</wurl:imageUrl>
  <wurl:xPosition>-5%</wurl:xPosition>
  <wurl:yPosition>-4%</wurl:yPosition>
  <wurl:opacity>0.3</wurl:opacity>
  <wurl:width>12%</wurl:width>
  <wurl:height>10%</wurl:height>
</wurl:watermark>
```

_Optional_. Tag to add a watermark into the transcode video. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

## Item Undelivered <a id="itemundelivered"></a>

Undeliverd fields are fields on supported and stored via MRSS ingestion but currently are not delivered to video services. They are optional fields that can be included in the case that Wurl and video services support them in the future. Each of these elements are are part of the `<item>` section of feed:

### Credit <a id="item-credit"></a>
```xml
<media:credit role="actor">Peter Dinklage</media:credit>
<media:credit role="director">Tim Van Patten</media:credit>
<media:credit role="author">David Benioff</media:credit>
```
_Optional_. Notable entity that contributed to the creation of the media object. May include actors, producers, studios, etc. [More...](http://www.rssboard.org/media-rss#media-credit)

### Copyright <a id="item-copyright"></a>
```xml
<media:copyright>Wurl 2018</media:copyright>
```
_Optional_. Copyright information for the video. [More...](http://www.rssboard.org/media-rss#media-copyright)

### Price <a id="item-price"></a>
```xml
<wurl:price type="rent" amount="19.99" currency="USD"/>
```
_Optional_. Pricing information about a media object. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

## ShortForm Video MRSS Example: <a id="shortform-example"></a>

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
      <media:category scheme="urn:wurl:external:id">123456-1</media:category>
      <media:category scheme="urn:iab:categories"
                  label="Video and Computer Games">IAB9-30</media:category>
      <media:category scheme="urn:roku:genre">Comedy</media:category>
      <media:category scheme="urn:samsung:genre">Drama</media:category>
      <media:rating scheme="urn:mpaa">pg-13</media:rating>
      <media:rating scheme="urn:v-chip">tv-y7-fv</media:rating>
      <wurl:closedCaptions type="SCC" lang="en-us" href="http://videos.com/en-us.scc"/>
      <wurl:closedCaptions type="SRT" lang="en-us" href="http://videos.com/en-us.srt"/>
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
      <media:thumbnail url="http://mysite.com/thumbnail/video-123.png"
                                                width="1920" height="1080"/>
      <wurl:watermark>
        <wurl:imageUrl>http://wurl-videos-dev.com/WM/asset/Foo_Logo.png</wurl:imageUrl>
        <wurl:xPosition>-5%</wurl:xPosition>
        <wurl:yPosition>-4%</wurl:yPosition>
        <wurl:opacity>0.3</wurl:opacity>
        <wurl:width>12%</wurl:width>
        <wurl:height>10%</wurl:height>
      </wurl:watermark>
    </item>
  </channel>
</rss>

```

## TV Series MRSS Example <a id="series-example"></a>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"
                   xmlns:dcterms="http://purl.org/dc/terms/"
                   xmlns:wurl="http://api.wurl.com/wurlrss/1.0"
                   xmlns:atom="http://www.w3.org/2005/Atom">
<channel>
  <atom:link rel="self" type="application/rss+xml"
                            href="http://www.myvideosite.com/newreleases.rss"/>
  <title>HBO - Game of Thrones</title>
    <link>http://www.hbo.com/game-of-thrones/index.html</link>
    <description>It’s not TV. It’s HBO</description>
    <pubDate>Thu, 10 Sep 2015 12:34:12 -0500</pubDate>
    <image>
       <url>http://www.hbo.com/240X240_logo.png</url>
       <title>HBO - Game of Thrones</title>
       <link>http://www.hbo.com/game-of-thrones/index.html</link>
    </image>
    <wurl:series>
      <wurl:officialTitle><![CDATA[Game of Thrones]]></wurl:officialTitle>
      <wurl:startYear>2011</wurl:startYear>
      <wurl:season>
         <wurl:seasonNumber>1</wurl:seasonNumber>
         <wurl:seasonTitle>Some title</wurl:seasonTitle>
      </wurl:season>
      <wurl:studio>n/a</wurl:studio>
    </wurl:series>
   <item>
      <title>Game of Thrones - Winter Is Coming</title>
      <link>http://www.hbo.com?series_id=123</link>
      <description>Robert Baratheon (King of the Seven Kingdoms of Westeros)
        and his Queen, Cersei Lannister...</description>
      <wurl:episode>
        <wurl:officialTitle><![CDATA[Winter Is Coming]]></wurl:officialTitle>
        <wurl:seasonNumber>1</wurl:seasonNumber>
        <wurl:episodeNumber>1</wurl:episodeNumber>
        <wurl:firstAired>Sun, 17 Apr 2011 00:00:00 -0000</wurl:firstAired>
      </wurl:episode>
      <wurl:price type="rent" amount="5.99" currency="USD"/>
      <media:content url="http://www.hbo.com?series_id=123" duration="5400"/>
      <media:thumbnail height="180"
             url="http://www.hbo.com/123.jpg" width="320"/>
      <dcterms:valid>start=Tue, 02 Dec 2014 00:00:00 -0600;
              end=Tue, 30 Jun 2015 00:00:00 -0500;scheme=W3C-DTF</dcterms:valid>
      <media:category>Fantasy</media:category>
      <media:category scheme="urn:wurl:genre">Action</media:category>
      <media:credit role="actor">Sean Bean</media:credit>
      <media:credit role="actor">Michelle Fairley</media:credit>
      <media:credit role="actor">Peter Dinklage</media:credit>
      <media:credit role="director">Tim Van Patten</media:credit>
      <media:credit role="author">David Benioff</media:credit>
      <media:rating scheme="urn:v-chip">tv-y7-fv</media:rating>
      <media:category scheme="urn:wurl:tms:series:id">SH1234</media:category>
      <media:category scheme="urn:wurl:tms:episode:id">EP1234</media:category>
      <media:category scheme="urn:wurl:ads:content:id">ABC123</media:category>
      <wurl:closedCaptions type="SCC" lang="en-us"
            href="http://wurl.com/en-us.scc"/>
      <guid isPermaLink="true">http://www.hbo.com?series_id=123</guid>
  </item>
  </channel>
</rss>

```

## Movie MRSS Example: <a id="movie-example"></a>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"
                   xmlns:dcterms="http://purl.org/dc/terms/"
                   xmlns:wurl="http://api.wurl.com/wurlrss/1.0"
                   xmlns:atom="http://www.w3.org/2005/Atom">
<channel>
  <atom:link rel="self" type="application/rss+xml"
                            href="http://www.myvideosite.com/newreleases.rss"/>
  <title>New Releases</title>
    <link>http://www.myvideosite.com/vod</link>
    <description>MyVideoSite provides an unmatched VoD
          services with over 3000 titles of pay and free content</description>
    <pubDate>Thu, 10 Sep 2015 12:34:12 -0500</pubDate>
    <image>
       <url>http://www.myvideosite.com/240X240_logo.png</url>
       <title>New Releases</title>
       <link>http://www.myvideosite.com/vod</link>
    </image>
   <item>
      <title>Jingle All The Way 2</title>
      <link>http://www.myvideosite.com?movieid=123</link>
      <description>JINGLE ALL THE WAY 2 - A heartwarming family
                              comedy starring Larry the Cable Guy</description>
      <wurl:movie>
        <wurl:officialTitle><![CDATA[Jingle All The Way 2]]>
                                                        </wurl:officialTitle>
        <wurl:year>2011</wurl:year>
      </wurl:movie>
      <wurl:price type="rent" amount="19.99" currency="USD"/>
      <media:content url="http://myvideosite.com/videos/123.mp4"
                                                       duration="5400"/>
      <media:thumbnail height="180"
             url="http://www.myvideosite.com/thumbnails/123.jpg" width="320"/>
      <dcterms:valid>start=Tue, 02 Dec 2014 00:00:00 -0600;
            end=Tue, 30 Jun 2015 00:00:00 -0500;scheme=W3C-DTF</dcterms:valid>
      <media:category>New Releases, Family, Holiday Season</media:category>
      <media:credit role="actor">Brian Stepanek</media:credit>
      <media:credit role="actor">Larry the Cable Guy</media:credit>
      <media:credit role="actor">David Milchard</media:credit>
      <media:credit role="director">Alex Zamm</media:credit>
      <media:credit role="author">Joe Doe</media:credit>
      <media:rating scheme="urn:mpaa">pg-13</media:rating>
      <guid isPermaLink="true">http://myvideosite.com/videos/123.mp4</guid>
  </item>
  </channel>
</rss>

```

