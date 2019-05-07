# ![LOGO](logo.png) NPR Listening Service **flow**ground Connector

## Description

A generated **flow**ground connector for the NPR Listening Service API (version 2).

Generated from: https://api.apis.guru/v2/specs/npr.org/listening/2/swagger.json<br/>
Generated at: 2019-05-07T17:43:17+03:00

## API Description

Audio recommendations tailored to a user's preferences

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Get a set of recommendations for an aggregation

> This endpoint provides a list of recent audio items associated with the aggregation along with metadata about the aggregation.

#### Input Parameters
* `aggId` - _required_ - ID of an aggregation such as a program or podcast
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `startNum` - _optional_ - The result to start with. Allows paging through the episodes of a podcast or program, with the default, `startNum=0`, being the most recent episode

### Get the list of available channels

> These channels allow the user to specify a focus for the content returned in the recommendations endpoint.

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `exploreOnly` - _optional_ - If set to `true`, this call will return only channels that should be shown in the client's `Explore` view

### Get recent ratings the logged-in user has submitted

> This endpoint provides the list of recently-rated audio recommendations that the logged-in user has consumed. Some rated recommendations are filtered, such as sponsorship and donation.

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.

### Get a list of recommendations from a category of content from an organization

> This endpoint provides a list of recommendations from a category of content from  an organization.

#### Input Parameters
* `orgId` - _required_ - ID of an organization, such as an NPR One station
* `category` - _required_ - One of the three categories of content - newscast, story, or podcast
    Possible values: newscast, story, podcast.
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.

### Get a variety of details about an organization including various lists of recent audio items

> This endpoint provides a variety of details about an organization including various lists of recent audio items.

#### Input Parameters
* `orgId` - _required_ - ID of an organization, such as an NPR One station
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.

### Retrieve the most recent promo audio heard by the logged-in user

> Gets the most recently played promo for which the user has neither tapped through the promo or listened to the target story.

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.

### Collect new ratings for media previously recommended to the logged-in user

> This endpoint is the main mechanism for providing feedback from the user to NPR about the recommendations that are obtained from `GET /listening/v2/recommendations`.<br/>
> <br/>
> A fully-populated link to this endpoint is returned with each individual recommendation and is located in the AudioItemDocument under the `links['recommendations']` object. The query parameters in this link should not be modified.<br/>
> Be sure to copy and send back the entire ratings object (RatingData), as new fields may be added to it in the future.<br/>
> <br/>
> This endpoint can return a blank JSON.doc or AudioItemDocument depending on the `recommend=true|false` parameter. The `recommend=true` flag allows this endpoint to both receive ratings and send back recommendations in the same call.

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `X-Advertising-ID` - _optional_ - A device-specific advertising identifier, if possible. Apple's IDFA is an example.
* `channel` - _optional_ - Determines the focus of the recommendations returned. Channel `npr` is recommended for most use cases.
    Possible values: npr, followed, recommended, emailstories, emailprograms, lapsedusersemail, ongoing email, newscasts, shows.
* `recommend` - _optional_ - If set to `false`, this call will return a blank document; otherwise it will return a new recommendation object

### Get a list of media for the logged-in user from NPR's recommendation engine

> This endpoint returns a list of audio recommendations. It is designed to be used for an initial list of recommendations, and then `GET /listening/v2/ratings?recommend=true` should be used for subsequent requests for recommendations.<br/>
> <br/>
> A fully-populated link to the ratings endpoint is returned with each individual recommendation and is located in the AudioItemDocument under the `links['recommendations']` object. The query parameters in this link should not be modified.<br/>
> Be sure to copy and send back the entire ratings object (RatingData), as new fields may be added to it in the future.

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `X-Advertising-ID` - _optional_ - A device-specific advertising identifier, if possible. Apple's IDFA is an example.
* `channel` - _optional_ - Determines the focus of the recommendations returned. Channel `npr` is recommended for most use cases.
    Possible values: npr, followed, recommended, emailstories, emailprograms, lapsedusersemail, ongoing email, newscasts, shows.
* `sharedMediaId` - _optional_ - This media was shared directly with the user; if provided, the service will add this recommendation to the top of the list
* `notifiedMediaId` - _optional_ - The user received a push notification about this media; if provided, the service will add this recommendation to the top of the list

### Get a list of recent audio and aggregation items associated with search terms

> In the schema shown below, SearchItemDocument is not an actual type of returned object; the object returned by a search will be either an AggregationAudioItemListDocument or an AudioItemDocument.

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `searchTerms` - _required_ - Search terms to search on; can include URL-encoded punctuation

## License

**flow**ground :- Telekom iPaaS / npr-org-listening-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
