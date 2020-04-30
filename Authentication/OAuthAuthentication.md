# OAuth User Authentication

Authentication with the Bonfire API is in compliance with the [OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749).

The Creator Toolkit does not currently support User OAuth. Instead, you can create Access Tokens for your Application's Bots.

### Authentication Flow

To Authenticate a Bot, you must have the Bot's ID available. If you have not yet registered a Bot, see [Creating a Bot](../../Resources/Bot.md).

```
POST -> /v1/oauth/bots
  + grant_type: "client_credentials"
  + bots (json array)
    + {botId}
    + (optional) {botId}
```
--
```
200 OK
```
```JSON
{
    "data": {
        "tokens": {
            "-OoX6R1ba0eM5kwmB8n": {
                "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjEtNTgxLTExLTE1ODgyMjY1NjUyOTMyMDQzOTc2MTE1Nzg4MTkxIn0.eyJpc3MiOiJCb25maXJlLUFQSS1Cb3QtQWNjZXNzIiwiYXVkIjoiZTA3ZmY0NmItZTJmNi00OWU1LWYyM2YtYzlkNjA4ODViYmE1IiwiaWF0IjoxNTg4MjI2NTY1LCJqdGkiOiIxLTU4MS0xMS0xNTg4MjI2NTY1MjkzMjA0Mzk3NjExNTc4ODE5MSIsImFpZCI6MSwiYmlkIjo1ODEsImF0aWQiOjExLCJzaWQiOjEsInR5cGUiOiJhY2Nlc3M6Ym90Iiwic2NvcGUiOiJ1c2Vycyxwb3N0cyxjYW1wcyIsInYiOjF9.3l8e2PfHQ8ms76tBiJZMT9SJKwf5PPtyGy_i0x-hrOI",
                "created_at": "2020-04-30T06:02:45+00:00",
                "scope": "users,posts,camps"
            }
        }
    }
}
```

*Note: The response `data` field SHALL be an [Access Token Object](OAuthAuthentication/AccessToken.md).*

The returned `access_token` attribute field can be used in [request authentication](RequestAuthentication.md) for future requests.

---

When the Access Token is no longer valid, but clients need to make an authenticated request, they MAY refresh the token. See the [Access Token Object](OAuthAuthentication/AccessToken.md#using-an-access-token) for more information on detecting invalid/expired Access Tokens.

To refresh an Access Token, submit the `refresh_token`, returned in the above response, to the OAuth endpoint with `grant_type=refresh_token`.

```
POST -> /v1/oauth
  + grant_type: "refresh_token"
  + refresh_token
```
--
```
200 OK
```
```JSON
{
    "data": {
        "id": 37,
        "type": "access_token",
        "attributes": {
            "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjItZGV2LW1vYi0yLTE1NTg3NDE5MTgtODk2NDMyMDk2MjcyODc1MDkxMiJ9.eyJpc3MiOiJSb29tcy1BUEktSW50ZXJuYWwtQWNjZXNzIiwiYXVkIjoiOTk5ZmMzMjEtNjkyNC00NzhkLWU2NmItNGVjMDYxODBmODQzIiwianRpIjoiMi1kZXYtbW9iLTItMTU1ODc0MTkxOC04OTY0MzIwOTYyNzI4NzUwOTEyIiwiaWF0IjoxNTU4NzQxOTE4LCJleHAiOjE1NTg4MjgzMTgsInRva2VuX3R5cGUiOiJhY2Nlc3MiLCJ0eXBlIjoidXNlciIsInVpZCI6MiwibGlkIjozMSwiYXRpZCI6Mzd9.C2Gr-jFJar_lFRFCC01geL9f7Xxx91ObW4IkLpbvPkU",
            "refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjItMi0xNTU4NzQxOTE4LXJlZnJlc2gtMjUxMjc0NzU4ODExMTA3ODc3MiJ9.eyJpc3MiOiJSb29tcy1BUEktSW50ZXJuYWwtUmVmcmVzaCIsImF1ZCI6Ijk5OWZjMzIxLTY5MjQtNDc4ZC1lNjZiLTRlYzA2MTgwZjg0MyIsImp0aSI6IjItMi0xNTU4NzQxOTE4LXJlZnJlc2gtMjUxMjc0NzU4ODExMTA3ODc3MiIsImlhdCI6MTU1ODc0MTkxOCwidG9rZW5fdHlwZSI6InJlZnJlc2giLCJ0eXBlIjoidXNlciIsInVpZCI6MiwibGlkIjozMSwiYXRpZCI6Mzd9.cYYjHOHH9Z6HgHdFEQt93FN2YDil87b1jIF3yXFIhSU",
            "expires_at": "2019-05-25T23:51:58+0000",
            "scope": "mob"
        }
    }
}
```

*Note: The response `data` field SHALL be an [Access Token Object](OAuthAuthentication/AccessToken.md).*

### Errors

There are numerous [error codes](../Errors.md) which can be returned during User Authentication.

