# Wurl MRSS Tags

This document covers the custom RSS elements (tags) for the Wurl namespace.


## Namespace declaration

```
<rss version="2.0" xmlns:wurl="http://api.wurl.com/wurlrss/1.0">
```

### `channel` tags

#### Series Info

If the feed contains a series, this tag may be used to include additional series information. If this tag is added on the channel level, only the `<wurl:episode>` tag have to be added on the item level.

| Element                  | Description                                                                | Data type | Example
|--------------------------|----------------------------------------------------------------------------|------------|---------------------------------
| `<wurl:series>`          | wurl:series start element.                                                 |            |
| `<wurl:officialTitle>`   | **Required**. Official Series title.                                       | String     | Game of Thrones
| `<wurl:startYear>`       | **Required**. The year the series started.                                 | Integer    | 2011
| `<wurl:studio>`          | **Optional**. The studio name.                                             | String     | HBO
| `<wurl:season>`          | wurl:season start element. Required if the series has seasons.             |            |
| `<wurl:seasonNumber>`    | **Required**. The series season number.                                    | Integer    | 1
| `<wurl:seasonTitle>`     | **Optional**. The season title.                                            | String     | Join the Game
| `</wurl:season>`         | wurl:season end element.                                                   |            |
| `</wurl:series>`         | wurl:series end element.                                                   |            |


### `item` tags

#### Episode Info

If the item is an episode belonging to a series, this tag may be used to include additional episode information.

| Element                  | Description                                                                | Data type | Example
|--------------------------|----------------------------------------------------------------------------|------------|---------------------------------
| `<wurl:episode>`         | wurl:episode start element.                                                |            |
| `<wurl:officialTitle>`   | **Required**. Official Episode title.                                      | String     | Winter Is Coming
| `<wurl:seasonNumber>`    | **Required**. The series season number.                                    | String     | 1
| `<wurl:episodeNumber>`   | **Required**. The episode number.                                          | Integer    | 3
| `<wurl:firstAired>`      | **Optional**. When the episode was first aired. RFC-822 date-time.         | Date       | Thu, 10 Sep 2015 12:00:00 GMT
| `</wurl:episode>`        | wurl:episode end element.                                                  |            |

-
#### Movie Info

If the item is a VOD movie, this tag may be used to include additional movie related information.

| Element                  | Description                                                                | Data type | Example
|--------------------------|----------------------------------------------------------------------------|------------|---------------------------------
| `<wurl:movie>`           | wurl:movie start element.                                                  |            |
| `<wurl:officialTitle>`   | **Required**. Official Movie title.                                        | String     | Star Wars: The Force Awakens
| `<wurl:year>`            | **Required**. The year the movie was released.                             | Integer    | 2015
| `</wurl:movie>`          | wurl:movie end element.                                                    |            |

-

#### Price Info

This tag is intended for including price information for VOD items.

| Element                  | Attribute           | Description                                          | Data type  | Example
|--------------------------|---------------------|------------------------------------------------------|------------|---------------------------------
| `<wurl:price>`           | type                | 'rent', 'purchase' or 'subscription'.                | String     | rent
| `<wurl:price>`           | amount              | Price amount of the media object.                    | String     | 5.99
| `<wurl:price>`           | currency            | [ISO 4217](http://en.wikipedia.org/wiki/ISO_4217)    | String     | USD

-

#### Cue Points

This item level tag is intended for signaling where mid-roll ads may be inserted in your video.

| Element                  | Attribute           | Description                                          | Data type  | Example
|--------------------------|---------------------|------------------------------------------------------|------------|---------------------------------
| `<wurl:cuepoints>`       | n/a                 | Comma separated cue points in seconds.               | String     | 10,20,30

-

#### Closed Captions

This item level tag is intended for including closed captions. You can have many of these for different languages.

| Element                  | Attribute           | Description                                          | Data type  | Example
|--------------------------|---------------------|------------------------------------------------------|------------|---------------------------------
| `<wurl:closedCaptions>`  | type                | WebVTT, SCC, STL, DFXP, TTML, SMPTE-TT, CAP, etc     | String     | SCC
| `<wurl:closedCaptions>`  | lang                | Language given in RFC 3066.                          | String     | en-us
| `<wurl:closedCaptions>`  | href                | Url to a closed captions file.                       | String     | http://wurl.com/en-us.scc

-

### Series Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"
                   xmlns:dcterms="http://purl.org/dc/terms/"
                   xmlns:wurl="http://api.wurl.com/wurlrss/1.0"
                   xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
    <atom:link rel="self" type="application/rss+xml"
                            href="http://www.myvideosite.com/newreleases.rss"/>
    <title>Game of Thrones</title>
    <link>http://www.somevideosite.com/game-of-thrones/index.html</link>
    <description>Game of Thrones</description>
    <pubDate>Thu, 10 Sep 2015 12:34:12 -0500</pubDate>
    <image>
       <url>http://www.somevideosite.com/240X240_logo.png</url>
       <title>Game of Thrones</title>
       <link>http://www.somevideosite.com/game-of-thrones/index.html</link>
    </image>
    <wurl:series>
      <wurl:officialTitle><![CDATA[Game of Thrones]]></wurl:officialTitle>
      <wurl:startYear>2011</wurl:startYear>
      <wurl:season>
         <wurl:seasonNumber>7</wurl:seasonNumber>
         <wurl:seasonTitle>Some title</wurl:seasonTitle>
      </wurl:season>
      <wurl:studio>NBC</wurl:studio>
    </wurl:series>
    <item>
      <guid isPermaLink="true">http://www.somevideosite.com?series_id=123</guid>
      <title>Game of Thrones - Winter Is Coming</title>
      <link>http://www.somevideosite.com?series_id=123</link>
      <description>Robert Baratheon (King of the Seven Kingdoms of Westeros)
                              and his Queen, Cersei Lannister...</description>
      <media:content url="http://www.somevideosite.com?series_id=123" duration="5400"/>
      <media:thumbnail width="180" height="320" url="http://www.somevideosite.com/123.jpg"/>
      <media:category>Fantasy</media:category>
      <media:credit role="actor">Sean Bean</media:credit>
      <media:credit role="actor">Michelle Fairley</media:credit>
      <media:credit role="actor">Peter Dinklage</media:credit>
      <media:credit role="director">Tim Van Patten</media:credit>
      <media:credit role="author">David Benioff</media:credit>
      <media:rating scheme="urn:v-chip">tv-y7-fv</media:rating>
      <wurl:price type="rent" amount="19.99" currency="USD"/>
      <dcterms:valid>start=Tue, 02 Dec 2014 00:00:00 -0600;
           end=Tue, 30 Jun 2015 00:00:00 -0500;scheme=W3C-DTF</dcterms:valid>
      <wurl:episode>
        <wurl:officialTitle><![CDATA[Winter Is Coming]]></wurl:officialTitle>
        <wurl:seasonNumber>1</wurl:seasonNumber>
        <wurl:episodeNumber>1</wurl:episodeNumber>
        <wurl:firstAired>Sun, 17 Apr 2011 00:00:00 -0000</wurl:firstAired>
      </wurl:episode>
      <wurl:cuepoints>910,1536,4319</wurl:cuepoints>

    </item>
  </channel>
</rss>
```

### VOD Movie Example
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
    <link>http://www.somevideosite.com/new-releases/index.html</link>
    <description>New Releases</description>
    <pubDate>Thu, 10 Sep 2015 12:34:12 -0500</pubDate>
    <image>
       <url>http://www.somevideosite.com/240X240_logo.png</url>
       <title>New Releases</title>
       <link>http://www.somevideosite.com/new-releases/index.html</link>
    </image>
    <item>
      <guid isPermaLink="true">http://www.somevideosite.com?movie_id=123</guid>
      <title>American Sniper (HD)</title>
      <link>http://www.somevideosite.com?movie_id=123</link>
      <description>Navy S.E.A.L. sniper Chris Kyle's
                                          pinpoint accuracy...</description>
      <wurl:movie>
        <wurl:officialTitle><![CDATA[American Sniper]]></wurl:officialTitle>
        <wurl:year>2014</wurl:year>
      </wurl:movie>
      <wurl:price type="rent" amount="9.99" currency="USD"/>
      <dcterms:valid>start=Tue, 02 Dec 2014 00:00:00 -0600;
           end=Tue, 30 Jun 2015 00:00:00 -0500;scheme=W3C-DTF</dcterms:valid>
      <media:content url="http://www.somevideosite.com?movie_id=123" duration="5400"/>
      <media:thumbnail width="180" height="320" url="http://www.somevideosite.com/123.jpg"/>
      <media:category>Action</media:category>
      <media:credit role="actor">Bradley Cooper</media:credit>
      <media:credit role="actor">Sienna Miller</media:credit>
      <media:credit role="director">Clint Eastwood</media:credit>
      <media:rating scheme="urn:mpaa">r</media:rating>
      <wurl:cuepoints>910,1536,4319</wurl:cuepoints>
      <wurl:closedCaptions type="SCC" lang="en-us" href="http://wurl.com/en-us.scc"/>
    </item>
  </channel>
</rss>
```

