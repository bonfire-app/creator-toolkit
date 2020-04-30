# Request Authentication

ALL requests to the API must be authenticated. There are currently two request authentication types:

* [Application-only Authentication](#application-only-authentication)
* [User Authentication](#user-authentication)

To authenticate a request, you must send the following header:

```
Authorization: Bearer {token}
```

Failing to provide any authentication headers will yield an [error response](../Schema.md#error-response) with error code [`400`](../Errors.md#error-codes).

The API allows **most** `GET` requests to be executed without user authentication, however; in this instance, application-only auth must be attempted.

## Application-only Authentication

Making requests to endpoints which do not require a User scope (such as OAuth, etc.) can be done using the application's App Key.

You will receive your App Key and App Secret along with your registration confirmation.

**You must store thse credentials securely and safely**. This API Key SHALL serve as the Bearer token described above.

## User Authentication

Some endpoints **require** a User scope to perform their functions. In this instance, you must perform [User Authentication](OAuthAuthentication.md#authentication-flow) and use the returned [Access Token](OAuthAuthentication/AccessToken.md#using-an-access-token) value which SHALL serve as the Bearer token described above. 
