# Wurl Feed Specifications

This is the Wurl feed specification covering the formats we prefer to use for inbound feeds to the Wurl Platform as well as outbound feeds.


## Content Types
A feed may contain one or more of the following types of content:

* Movies
* Series
* TV Specials
* Short-form videos i.e. the content is not TV Shows or Movies


## Feed Formats

### JSON Feed Format

This is a JSON format that is supported for all types of content, including Movies, Series and TV Specials that require detailed metadata. See [JSON Feed Specification](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-json-feed-specification.md) for details.

### MRSS Feed Format

When using MRSS, please provide Wurl with a syndication feed in standard RSS 2.0/MRSS format. Wurl requires some additional Wurl defined tags in order to ingest additional meta data that is not covered in the standard specification. See [Wurl MRSS Feed format](https://github.com/wurlinc/wurl-feed-specifications/blob/master/mrss-feed-spec.md).

#### Resources

| Reference                                      | URL
|-------------------------------------------     | ----------
| XML 1.0 Specification                          | <http://www.w3.org/TR/REC-xml/>
| RSS 2.0 Specification                          | <http://www.rssboard.org/rss-specification>
| Media RSS Specification                        | <http://www.rssboard.org/media-rss>
| Dublin Core Specification                      | <http://dublincore.org/documents/dc-xml-guidelines/>
| W3C Feed Validation Service                    | <https://validator.w3.org/feed/>
| Wurl MRSS Tags                                 | [Wurl MRSS Tags](https://github.com/wurlinc/wurl-feed-specifications/blob/master/wurl-mrss-namespace.md)



