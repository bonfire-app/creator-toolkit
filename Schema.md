# Bonfire Response Schema

All response headers SHALL follow the [HTTP/1.1 status codes definitions](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html). 

All response bodies SHALL be JSON-encoded, and fully parsable by any standard JSON serializer.

At a fundamental level, there are two Bonfire API response types:

* [Success response](#success-response)
* [Error response](#error-response)

All resource endpoints MUST use one of these response formats. However; non-resource endpoints may have their own schema.

## Success Response

To qualify a success, the response MUST have a `2xx`/`3xx`-level HTTP status code, MUST NOT have an `error` field,
and MAY include a `data` field. e.g.:

```
GET -> /v1/users/me
```
--
```
200 OK
```
```
{
    "data": {
        "id": "-OXenJM65bX4K1m2xAQ",
        "type": "user",
        "attributes": {
            "identifier": "Pasquale",
            "display_name": "Pasquale",
            "color": "F5C23B",
            "media": {
                "avatar": {
                    "full": {
                        "url": "https://uploads.cdn.bonfire.camp/ZPp8vZ.jpg"
                    }
                }
            },
            "created_at": "2019-07-26T17:13:01+00:00",
            "suspended": false,
            "verified": false,
            "summaries": {
                "counts": {
                    "posts": 21,
                    "following": 3,
                    "camps": 10
                }
            },
            "bio": "I love to download and upload",
            "location": {
                "display_text": "New York"
            },
            "website": {
                "action_url": "http://pasquale.cool",
                "display_url": "http://pasquale.cool"
            }
        }
    }
}
```

*Note: Some success responses may include additional fields, such as the `meta` field.*

## Error Response

To qualify an error, the response MUST have a `4xx`/`5xx`-level HTTP status code, and MUST include the `error` field
which consists of an [error object](Errors.md#error-object). E.g.:

```
GET -> /v1/users/me/
```
--
```
401 Unauthorized
```
```
{
    "error": {
        "message": "Your request could not be completed because it was not properly authenticated.",
        "code": 400
    }
}
```