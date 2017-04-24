Language doForms [![Build Status](https://travis-ci.org/OpenFn/language-doforms.svg?branch=master)](https://travis-ci.org/OpenFn/language-doforms)
=================

Language Pack for building expressions and operations to interact with the [doForms API](http://www.doforms.com/wp-content/uploads/2015/10/web-services-guide.pdf).

According to the API documentation: "doForms web services MUST be connected to using SOAP. There are known problems with connecting to the web services via HTTP and we do not support this method."

This language package is a work in progress. We want to `getUnReadData` and then `markUnReadDataAsRead` as described in the doForms API documentation.

We will use roughly the same pattern as is used by "fetch" in [language-surveycto](https://github.com/OpenFn/language-http/blob/master/src/Adaptor.js#L42-L69) except that the `request.post` will be handled inside Adaptor.js, rather than in Client.js. (There is no Client.js for simplicity.)

**Note that an XML conversion package may be used. language-commcare uses 'js2xmlparser'.**
```js
import js2xmlparser from 'js2xmlparser';
```

Documentation
-------------
## fetch and mark as read

#### sample configuration
```json
{
  "username": "taylor@openfn.org",
  "password": "supersecret"
}
```

#### sample expression using operation
```js
fetchAndMarkRead({
  "endpoint": "api/v1/forms/",
  "form": "abc123",
  "returnUrl": "https://www.openfn.org/inbox/secret-inbox-id"
})
```

[Docs](docs/index)

Development
-----------

Clone the repo, run `npm install`.

Run tests using `npm run test` or `npm run test:watch`

Build the project using `make`.
