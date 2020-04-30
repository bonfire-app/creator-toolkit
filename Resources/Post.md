# `post` [Resource]

Posts are at the center of the Bonfire API ecosystem. They exist in many contexts, especially in Streams.

Posts have the following CRUD functions:

* Create (`POST -> /v1/users/me/posts`)
* Retrieve (`GET -> /v1/posts/{postID}`)
* Update (`PUT -> /v1/posts/{postID}`)
* Delete (`DELETE -> /v1/posts/{postID}`)

### Resource Object

The Post Resource is the most complex of all [Resource Objects](../Concepts/Resource.md#resource-object-types).

**Base Attributes:**

Type | Key | Description
---- | --- | -----------
string | `message` | The User-created body of the Post
array | `entities` | An array of [Post Entities](./Post/) contained in the `message`
object | [`details`] | The User-controlled attributes of the Post
object | [`status`] | The non User-controlled attributes of the Post
object | [`summaries`] | Summaries of Post-related attributes
object | [`context`] | A [Context Object] representing current User's relationship with the Post
 

### Example Object

```JSON
{
    "id": "97116",
    "type": "post",
    "attributes": {
        "message": "I hate ASMR",
        "entities": [],
        "creator": {
            "id": "-wb1ZJlEaLoZKN3MYAx",
            "type": "user",
            "attributes": {
                "identifier": "realsteven",
                "display_name": "Steven",
                "color": "FFBAB8",
                "media": {
                    "avatar": {
                        "full": {
                            "url": "https:\/\/uploads.cdn.bonfire.camp\/Vd2aaZ.jpg"
                        }
                    }
                },
                "created_at": "2020-04-24T18:10:03+00:00",
                "suspended": false,
                "verified": false
            }
        },
        "posted_in": {
            "id": "-LYk8gJw62nNr",
            "type": "camp",
            "attributes": {
                "identifier": "HotTakes",
                "title": "Hot Takes",
                "description": "Share your unpopular opinion with the world",
                "color": "FF0900",
                "media": {
                    "avatar": {
                        "full": {
                            "url": "https:\/\/uploads.cdn.bonfire.camp\/J01MW0.jpg"
                        }
                    }
                },
                "created_at": "2019-11-15T02:32:26+00:00",
                "suspended": false,
                "verified": false,
                "private": false
            }
        },
        "parent": null,
        "created_at": "2020-04-26T20:55:46+00:00",
        "context": {
            "post": {
                "permissions": {
                    "reply": [
                        "text",
                        "media\/img",
                        "media\/gif",
                        "media\/video",
                        "media\/text"
                    ],
                    "quote": true,
                    "delete": true
                }
            }
        },
        "summaries": {
            "replies": [],
            "counts": {
                "replies": 0
            }
        }
    }
}
```

*Note: the `context` object SHALL only be returned when [User Authentication] is present.*

[Resource]: ../ResourceObjects.md
[`details`]: Post/DetailsObject.md
[`status`]: Post/StatusObject.md
[`summaries`]: Post/SummariesObject.md
[`context`]: Post/ContextObject.md
[Context Object]: ../Generics/ContextObject.md
[User Authentication]: ../Authentication/RequestAuthentication.md#user-authentication
