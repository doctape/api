Introduction
================================================================================

The doctape API endpoint is located at `https://api.doctape.com`. Be sure to
send all your requests UTF-8 encoded over HTTPS.

Currently there's only one version of the doctape API, nameley v1. Always append
the version number to the base URL.

**Example**

    https://api.doctape.com/v1/


Libraries and tools
--------------------------------------------------------------------------------

 - There's an official
   <a href="https://github.com/doctape/doctape-client-js" target="_blank">
   doctape library</a> written in JavaScript for browser and node (available via
   <a href="https://npmjs.org/package/doctape" target="_blank">npm</a>).

 - <a href="https://npmjs.org/package/passport-doctape" target="_blank">
   passport.js module</a>

Let us know if you maintain a third party library that leverages the doctape
API and we'll add it to this list.


Authentication
--------------------------------------------------------------------------------

The doctape API uses a subset of the
<a href="http://tools.ietf.org/html/draft-ietf-oauth-v2-31" target="_blank">
OAuth 2.0 protocol</a> for authentication. To get started,
[log in](http://developer.doctape.com/auth/doctape) to create your first application right away. To gain an
access token, be sure to have a look at the detailed
[Authentication Guide](/auth.md) first.

JSONP AND CORS
--------------------------------------------------------------------------------

The doctape API supports both, JSONP and CORS, for easy, unauthenticated
cross-domain API requests.

Metadata
--------------------------------------------------------------------------------

Before files are processed, doctape collects [metadata](/metainformation.md) depending on
the file type, which you can access via the API.


Resources
--------------------------------------------------------------------------------

There's a [complete list of resources](/resources.md), be sure to check it out.


Response Format
--------------------------------------------------------------------------------

All operations except binary transfers return a JSON object with the keys
`error` and `result`.

If the operation succeeded, the HTTP status code is 200, `result` is populated
and `error` equals `null`.

    HTTP 200 OK
    {
      "error": null,
      "result": {
        ...
      }
    }

If the operation failed, the HTTP status code is greater than 400 , `result`
equals `null` and `error` is populated.

    HTTP 401 Unauthorized
    {
      "error": {
        "code": 401,
        "message": "Unauthorized"
      },
      "result": null
    }

Contact & Support
--------------------------------------------------------------------------------

Just send an email to developer@doctape.com.
