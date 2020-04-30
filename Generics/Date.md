# Dates

Most [Resource Objects](../Concepts/Resource.md) include an attributes field which represents a Date/DateTime.
All dates read in/out of the API shall be in [ISO 8601](https://www.w3.org/TR/NOTE-datetime) format, as below:

For instance, the date `August 14, 2019 @ 04:03:55am (UTC-4)` becomes `2019-08-14T04:03:55-04:00` when being passed into the API.

### Example

When loading a [Post](../Resources/Post.md), the `created_at` date must be parsed according to this spec to ensure proper handling. 

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
        "posted_in": null,
        "parent": null,
        "created_at": "2020-04-26T20:55:46+00:00",
        "summaries": {
            "replies": [],
            "counts": {
                "replies": 0
            }
        }
    }
}
```

### Value

In this example, `2020-04-24T18:10:03+00:00` would be the outputted date, which represents `April 24, 2020 @ 6:10:03 PM (UTC)`.
