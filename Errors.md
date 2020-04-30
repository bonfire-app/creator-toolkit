# Errors

Errors MUST always follow the [Error Response specification](Schema.md#error-response).

## Error Object

An error object is a JSON object which MUST include the following fields:

* `message`
* `code`

Error objects MAY additionally include the following fields:

* `params`

#### Examples

```
{
    "message": "Your request could not be completed because it was not properly authenticated.",
    "code": 400
}
```

You can read variables used in the error message (if any) by checking the `params` field.
```
{
    "message": "This user (kanyewest) does not exist.",
    "code": 702,
    "params": [
        "kanyewest"
    ]
}
```

## Error Codes

Code | Message | HTTP code | Description | Reference
---- | ------- | --------- | ----------- | ---------  
400 | Your request could not be completed because it was not properly authenticated. | 401 | Something was wrong with the authentication method for this request. | [Request Authentication](authentication/RequestAuthentication.md)
401 | A valid access token is required to access this resource. | 401 | | [Request Authentication](authentication/RequestAuthentication.md)
403 | Cannot generate a new phone authorization code, you must wait 30 seconds. | 401
410 | The client being used is out of date given the provided parameters. | 403 | The provided client version header is now out-of-date. | [Request Authentication](authentication/RequestAuthentication.md), [Client Identification](authentication/ClientIdentification.md)
420 | You must be authenticated as a user to take this action. | 401 | Identity required to make this request. | [User Authentication](authentication/OAuthAuthentication.md), [Request Authentication](authentication/RequestAuthentication.md)
450 | The provided access token is invalid, or cannot be used with the provided parameters. | 401 | Invalid or expired [Access Token](authentication/OAuthAuthentication/AccessToken.md) provided. | [User Authentication](authentication/OAuthAuthentication.md), [Access Token](Authentication/OAuthAuthentication/AccessToken.md)
451 | The provided refresh token is invalid, or cannot be used with the provided parameters. | 400 | Invalid Refresh Token provided. | [User Authentication](authentication/OAuthAuthentication.md), [Access Token](authentication/OAuthAuthentication/AccessToken.md)
452 | The provided access token or refresh token does not match the given bearer token. | 401 | Mismatched API Key provided when refreshing token. | [User Authentication](authentication/OAuthAuthentication.md)
460 | The provided refresh token cannot be used to renew an access token. Client login should be attempted. | 403 | | [User Authentication](authentication/OAuthAuthentication.md)
600 | The requested operation is not permitted on this resource. | 412 | A precondition was not met for this request. | 
610 | Could not take action on the resource with the given parameters. Please check the values provided and try again. | 400 | Could not take the requested action on the resource. | 
620 | Missing request parameter where required.<br><br>Missing request parameter '{param}'. | 412 | | 
621 | Invalid request parameter '{param}'. | 412 | | 
630 | The requested media does not exist or cannot be used at this time. | 412 | The media provided as a parameter in the request is invalid, or can no longer be used.
640 | Private Camps must have at least one manager. | 412 | The last administrator cannot leave a camp while there are still members. | 
650 | The provided identifier ({identifier}) is already being used. | 412 | | 
660 | No change occurred given the provided parameters. | 304 | Depending on your request serializer, you may or may not see the error object. A `304` HTTP status code will ALWAYS be this error. | 
670 | You cannot combine multiple media types as attachments. | 412 | | [link to Post media rules]
671 | The provided media type cannot be used in this request. | 412 | | [link to Room docs], [link to User docs]
700 | Could not take action because the resource did not exist. | 404 | The requested endpoint or resource does not exist. | 
 | | | | 
The below was auto-generated and should be checked |
 | | | | 
701 | No camp exists for the identifier {identifier}. | 404 | | 
702 | This user ({userID&#124;username}) does not exist. | 404 | | 
703 | This post ({postID}) does not exist in this camp, or has been removed. | 404 | | 
711 | This camp ({campID&#124;identifier}) has blocked your profile. | 401 | | 
712 | This user ({userID&#124;username}) has blocked your profile. | 401 | | 
720 | The provided search ({query}) is too complex. Try removing some keywords, operators, or both. | 412 | | 
730 | This action is not permitted because you do not have the necessary ownership permissions for this resource. | 401 | | 
740 | You have blocked this resource. | 401 | | 
800 | Your password must be reset before you can continue. | 409 | Error thrown during [User Authentication](authentication/OAuthAuthentication.md); Client should proceed to password reset for the User. | 
810 | Your profile has been suspended for violating our terms. Contact us if you believe this to be a mistake. | 409 | | 
820 | The provided email address ({email}) is already being used. | 412 | | 
830 | The provided username ({username}) is already being used. | 412 | | 
900 | Invalid HTTP method used for this endpoint. See params for supported methods. | 405 | Check error `params.methods` array for the endpoint's allowed HTTP methods. | [Error Object](#error-object) 
910 | The provided api version is invalid. | 400 | Check your request URL for api version. | [Request Versioning](README.md#versioning)
970 | A conflict exists in accessing the requested resource. | 409 | | 
980 | Something went wrong while communicating with our server. | 500 | | 