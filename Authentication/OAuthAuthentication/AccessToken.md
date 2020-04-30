# `access_token` [Object]

Access Tokens are a way for clients to identify themselves to the API when making requests.

Access Tokens have the following CRUD functions:

* Create (`POST -> /v1/oauth/bots`)

### Resource Object

Attributes:

Type | Key | Description
---- | --- | -----------
string | `access_token` | The raw Access Token value
string | `refresh_token` | The raw Refresh Token value
string | `expires_at` | The expiration date
string | `scope` | The scope for the Access Token

### Example Object

```JSON
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjItZGV2LW1vYi0yLTE1NTg3MTE1ODgtMzYzMzgxMzk3MTcxOTQzMTE2NyJ9.eyJpc3MiOiJSb29tcy1BUEktSW50ZXJuYWwtQWNjZXNzIiwiYXVkIjoiOTk5ZmMzMjEtNjkyNC00NzhkLWU2NmItNGVjMDYxODBmODQzIiwianRpIjoiMi1kZXYtbW9iLTItMTU1ODcxMTU4OC0zNjMzODEzOTcxNzE5NDMxMTY3IiwiaWF0IjoxNTU4NzExNTg4LCJleHAiOjE1NTg3OTc5ODgsInRva2VuX3R5cGUiOiJhY2Nlc3MiLCJ0eXBlIjoidXNlciIsInVpZCI6MiwibGlkIjozMSwiYXRpZCI6MzZ9.Jggm2lHLm9dsYPkwrRw1eNUPSDy1AbpOsgudgHsU2XM",
    "refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjItMi0xNTU4NzExNTg4LXJlZnJlc2gtODEzMjY5Njc5NjUzNDgzNTM1In0.eyJpc3MiOiJSb29tcy1BUEktSW50ZXJuYWwtUmVmcmVzaCIsImF1ZCI6Ijk5OWZjMzIxLTY5MjQtNDc4ZC1lNjZiLTRlYzA2MTgwZjg0MyIsImp0aSI6IjItMi0xNTU4NzExNTg4LXJlZnJlc2gtODEzMjY5Njc5NjUzNDgzNTM1IiwiaWF0IjoxNTU4NzExNTg4LCJ0b2tlbl90eXBlIjoicmVmcmVzaCIsInR5cGUiOiJ1c2VyIiwidWlkIjoyLCJsaWQiOjMxLCJhdGlkIjozNn0.Jd0BC1-XY-5SUTsV7qzkfzwhQ1rf7S6C-umSvKxMa6Y",
    "expires_at": "2019-05-25T15:26:28+00:00",
    "scope": "users,posts,camps"
}
```

## Using an Access Token

Access Tokens are valid from the DateTime that the request was initiated, until `expires_at`.
Requests initiated beyond this date will return an [error response](Schema.md#error-response) (error code [`450`](Errors.md#error-codes)).

To enable long-lived logins, Access Tokens can be refreshed using the `refresh_token` field. See the [User Authentication](../OAuthAuthentication.md) documentation for more information.

Clients MUST store the `access_token` raw value for use in subsequent User-authenticated requests. See [Request Authentication](../RequestAuthentication.md) for more info.

Clients MUST store the `refresh_token` raw value for later use. Clients MUST obide by the following methodologies for maintaining valid Access Tokens;

1. Store `expires_at` and ensure your request handler uses the cached `refresh_token` to get a new Access Token before `expires_at`
2. Make authenticated requests—using `access_token` raw value—until an error response with error code [`450`](Errors.md#error-codes), then use the cached `refresh_token` to get a new Access Token


[Object]: ../../Concepts/Object.md