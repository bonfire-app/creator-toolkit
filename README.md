# creator-toolkit
 
The Bonfire Creator Toolkit provides content creators an interface to the Bonfire API.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this repository are to be interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119).

## Changelog

A full changelog for the API, starting at v1.4.0 is available at /CHANGELOG.md.

## Requests

The Bonfire API is available at https://api.bonfire.camp/v1. Version 1 is the only available version.

## Getting Started

### Concepts

- [Objects]
- [Resources]

#### Docs
* [Response Schema](Schema.md)
    * [Successful Response](Schema.md#success-response)
        * [Resource Objects](./Concepts/Resource.md)
    * [Error Response](Schema.md#error-response)
* [OAuth User Authentication](Authentication/OAuthAuthentication.md)
* [Request Authentication](Authentication/RequestAuthentication.md)
* [Dates specification](Generics/Date.md)
* [Errors](Errors.md)

#### Resource Objects
* [Access Token](Authentication/OAuthAuthentication/AccessToken.md)
* [Post](Resources/Post.md)


[Objects]: Concepts/Object.md
[Resources]: Concepts/Resource.md