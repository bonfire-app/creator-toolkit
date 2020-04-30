# `post` Entity [Object]

The Post Entity object is dynamically generated on output based on the Post `message`. It contains any and all
syntactically relevant "entities". Today, this includes URLs, #CampTags and @Handles.


**Base Attributes:**

Type | Key | Description
---- | --- | -----------
string | `type` | The type of entity
string | `display_text` | The substring in the `message` to be wrapped in a link 
string (url) | `action_url` | The destination URL to follow. Clients MUST use this when link is clicked.
string (url) | `expanded_url` | The final-destination URL for the entity


### Camp Entity

Any occurrence of a #CampTag in a Post `message` should be replaced retroactively by clients using the below entity.

```json
{
    "type": "camp",
    "display_text": "#BonfireBugs",
    "action_url": "https://bonfire.camp/c/BonfireBugs",
    "expanded_url": "https://bonfire.camp/c/BonfireBugs",
}
```


### User Entity

Any occurrence of an @Handle in a Post `message` should be replaced retroactively by clients using the below entity.

```json
{
    "type": "profile",
    "display_text": "@emmamway",
    "action_url": "https://bonfire.camp/u/emmamway",
    "expanded_url": "https://bonfire.camp/u/emmamway"
}
```


### URL Entity

URL Entities are the most complex type of Entity. They have additional attributes unique to URLs.

**Additional Attributes:**

Type | Key | Description
---- | --- | -----------
array | `indices` | The indices in the `message` string where the link should be placed. Multi-byte chars counted as 1.



```json
{
    "type": "url",
    "display_text": "google.com",
    "action_url": "http://google.com",
    "expanded_url": "http://google.com",
    "indices": [
        10,
        20
    ]
}
```


[Object]: ../../Concepts/Object.md
