# Resource [Object]s

Resources in the API follow a strict format. All Resource Objects must include the following fields:

* `id` The resource logical ID
* `type` A string representing the resource type ([See below](#resource-object-types) for types)
* `attributes` An array of attributes relating to the resource. Each resource manages its own attributes formatting. See the resource's documentation for more info. 

## Resource Object Types

Currently, the API includes the following Resource Object types:

* [`application`](Authentication/OAuthAuthentication/Application.md)
* [`access_token`](Authentication/OAuthAuthentication/AccessToken.md)
* `refresh_token`
* `user`
* [`camp`](../Resources/Camp.md)
* [`post`](../Resources/Post.md)
* `media`

[Object]: ./Object.md 
