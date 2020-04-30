# Object (Abstract)

As per the [Response Schema specification]:

> All response bodies MUST be JSON-encoded, and fully parsable by any JSON serializer.

As such, response bodies MUST always be [JSON Objects](https://json-schema.org/understanding-json-schema/reference/object.html), allowing us to communicate
multiple fields in responses. See the [Response Schema specification] for more information. 

---

Objects are usually contained within [Resources] to communicate complex data values in API Resources, but Resources
are themselves, Objects.

[Response Schema specification]: ../Schema.md
[Resources]: Resource.md