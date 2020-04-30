# `context` Object (Abstract)

Context Objects are a way to communicate the relationship between two [Resources](../Concepts/Resource.md), usually a User and some other object.

### IMPORTANT

Many Resources specify that they **MAY** have a `context` attribute; however, this SHALL only be the case when [User Authentication](../Authentication/RequestAuthentication.md#user-authentication) is present.

### Context Attributes

 Implementations of the Context Object SHALL exist in the `context` attribute of the requested Resource. The actual implementation of the context object is outside the scope of this document, but SHALL be specified in Context Object implementations.
