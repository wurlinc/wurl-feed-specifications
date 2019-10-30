# MRSS feed format for Movie or TV series providers


This page describes the MRSS format Movie or TV series providers should use to add their content to the Wurl Platform. As appropriate, include the elements below to convey episodic content spanning multiple seasons, viewing "windows", pricing information etc. VOD movies and series should be made available in separate feeds. For series that has seasons we recommend one feed per season. Wurl will transcode your videos to ensure playback on a variety of devices. The format of your videos you provide in the feed need to conform to the [Mezzanine Specification](https://github.com/wurlinc/wurl-feed-specifications/blob/master/recommended-video-formats.md).


Before submitting your feed to Wurl, make sure your feed validates using one of the available validation tools.

## Elements in `<channel>` section of your syndication feed:

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


## Your syndication feed should contain multiple `<item>` groups, one for each video. Elements in `<item>` section of feed:

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

### Genres
```xml
<media:category scheme="urn:wurl:genre">Cooking</media:category>
```
Assigns a genre. Video Service specific genres can be added like this:

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

### TMS
```xml
<media:category scheme="urn:wurl:tms:series:id">SH1234</media:category>
<media:category scheme="urn:wurl:tms:episode:id">EP1234</media:category>
```
Assigns a TMS Series or Episode ID.

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
_Required if series feed_. Episode tag containing series info. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Wurl Movie
```xml
<wurl:movie>
  <wurl:officialTitle><![CDATA[Jingle All The Way 2]]></wurl:officialTitle>
  <wurl:year>2011</wurl:year>
</wurl:movie>
```
**Required if movie feed**. Movie tag containing series info. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Valid
```xml
<dcterms:valid>start=Tue, 02 Dec 2014 00:00:00 -0600;end=Tue, 30 Jun 2015 00:00:00 -0500;scheme=W3C-DTF</dcterms:valid>
```
Start and end date indicating the time period the video is available for viewing. See example below.

### Price
```xml
<wurl:price type="rent" amount="19.99" currency="USD"/>
```
Optional tag to include pricing information about a media object. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### ClosedCaptions
```xml
<wurl:closedCaptions type="SCC" lang="en-us" href="http://wurl.com/en-us.scc"/>
```
Optional tag to include closed captions. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Rating
```xml
<media:rating scheme="urn:mpaa">pg-13</media:rating>
```
This allows the permissible audience to be declared. [More...](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)

### Watermark

In order to add a watermark into the transcode video the tag below can be used for that purpose. Properties:

- **url** - url to png file
- **x** - x coordinate can be pixel or percentage - e.g. -10% is 10% from right side
- **y** - y coordinate can be pixel or percentage - e.g. -10% is 10% from bottom side
- **opacity** - from 1.0 to 0.0 where 0.0 is fully transparent - e.g. 0.3
- **width** - percentage size of original image - e.g. 10
- **height** - percentage size of original image - e.g. 10

```
<wurl:watermark>
  <wurl:imageUrl>http://wurl-videos-dev.com/WM/asset/Foo_Logo.png</wurl:imageUrl>
  <wurl:xPosition>-5%</wurl:xPosition>
  <wurl:yPosition>-4%</wurl:yPosition>
  <wurl:opacity>0.3</wurl:opacity>
  <wurl:width>12%</wurl:width>
  <wurl:height>10%</wurl:height>
</wurl:watermark>
```

## Movie MRSS Example:

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

## TV Series MRSS Example:

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
