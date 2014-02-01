<a id="top"></a>
Authentication
================================================================================

The doctape API uses a subset of the
<a href="http://tools.ietf.org/html/draft-ietf-oauth-v2-31" target="_blank">
OAuth 2.0 protocol</a> for API authentication.

doctape supports the use of bearer tokens as access tokens. To gain such an
access token, follow either the [Authorization Code Grant]
(#authorization_code_grant) flow or the [Implicit Grant](#implicit_grant) flow.

After you successfully gained an **access token**, you can use it to
authenticate your requests. doctape supports the use of bearer tokens as access
tokens. Just send the following header along with all your HTTP
requests:

    Authorization: Bearer [access_token]

> It's also possible to send the **access token** via the query string, which
> can be useful to make non-XHR requests like binary transfers from the users
> browser.
>
> Example: `GET https://api.doctape.com/v1/doc?access_token={access_token}`
>
> **Warning**: Query string should only be used when necessary (e.g. for binary
> transfers). The risk that access tokens are logged is much higher this way.

Be sure to also learn about the [lifetime of tokens](#lifetime_of_tokens), the
[list of supported scopes](#supported_scopes) and the error handling.


<a id="authorization_code_grant"></a>
Authorization Code Grant
--------------------------------------------------------------------------------

This is the easiest way to get an access token – use it for server-side
applications with languages like Ruby, Python or PHP.

 1. Direct a user to this URL:

        https://my.doctape.com/oauth2
            ?client_id=[your client id]
            &response_type=code
            &redirect_uri=[your redirect URI]
            &scope=[scopes separated by spaces]
            &state=[any string to prevent CSRF attacks]

    > Have a look at the [complete list of scopes](#supported_scopes).
    >
    > <a href="http://en.wikipedia.org/wiki/Cross-site_request_forgery"
         target="_blank">CSRF: Cross-site request forgery</a>

    After the redirect, the user will be asked to log into his doctape account
    and grant the requested scopes to the application.

    > The `state` parameter is optional but should be set to a unique value.
      Later on, this parameter will be appended to the answer, so that your
      application can check state.

 2. After the user decided to authorize your application, he is redirected to:

        https://[your redirect URL]/?code=[CODE]
                                    &state=[your string to prevent CSRF attacks]

    > We strongly recommend the use of https to secure the transfered access
    > tokens and auth codes.

 3. Your server application must then extract the `code` parameter and make a
    **POST** request to:

        https://my.doctape.com/oauth2/token

    with an URL-encoded body:

        client_id=[your client id]
        &client_secret=[your client secret]
        &grant_type=authorization_code
        &redirect_uri=[your redirect URI]
        &code=[extracted code parameter]

    **Important**: Be sure to keep your client secret confidential.

    > For security reasons, the `code` parameter is only valid for 10 minutes
      and single-time use.

 4. doctape will respond with JSON-encoded data like this:

        {
          "access_token": "[your access token]",
          "token_type": "Bearer",
          "expires_in": 157680000,
          "refresh_token": "[deprecated]"
        }

    > Access tokens expire after 5 years for security reasons.

Awesome! You now have a valid access token to make authorized requests to the
[doctape API](/resources.md).

-----
> [back to top](#top)

-----

<a id="implicit_grant"></a>
Implicit Grant
--------------------------------------------------------------------------------

If you're building a client-side browser application, you have to use the
implicit grant flow.

 1. Direct a user to this URL:

        https://my.doctape.com/oauth2
            ?client_id=[your client id]
            &response_type=token
            &redirect_uri=[your redirect URI]
            &scope=[scopes separated by spaces]
            &state=[any string to prevent CSRF attacks]

    > Have a look at the [complete list of scopes](#supported_scopes).
    >
    > <a href="http://en.wikipedia.org/wiki/Cross-site_request_forgery"
         target="_blank">CSRF: Cross-site request forgery</a>

    After the redirect, the user will be asked to log into his doctape account
    and grant the requested scopes to the application.

    > The `state` parameter is optional but should be set to a unique value.
      Later on, this parameter will be appended to the answer, so that your
      application can check state.

 2. After the user decided to authorize your application, he is redirected to:

        https://[your redirect URL]#access_token=[access token]
                                   &token_type=Bearer
                                   &expires_in=157680000
                                   &state=[your string to prevent CSRF attacks]

    > We strongly recommend the use of https.

Awesome! You now have a valid access token to make authorized requests to the
[doctape API](/resources.md). Access tokens are valid for 5 years after
creation.

-----
> [back to top](#top)

-----


<a id="lifetime_of_tokens"></a>
Lifetime of Tokens
--------------------------------------------------------------------------------

doctape limits the lifetime and access numbers of codes and tokens for security
reasons:

 - Authorization codes are valid 10 minutes and single-use.
 - Access tokens are valid 5 years.

-----
> [back to top](#top)

-----

<a id="supported_scopes"></a>
Supported Scopes
--------------------------------------------------------------------------------

doctape supports the following scopes:

 - account.read: receive information about a user
 - file.create: upload or clone files
 - file.read: list and read files
 - file.update: modify files
 - file.delete: delete files
 - tape.read: list and read tapes
 - tape.update: modify tapes

If no scope is given, scope is set to `account.read`.

-----
> [back to top](#top)

-----

<a id="error_handling"></a>
Error Handling
--------------------------------------------------------------------------------

If any request fails, doctape redirects the user to the given redirect URL and
appends an `error` parameter to the query string, containing a error code.
Checkout the
<a href="http://tools.ietf.org/html/draft-ietf-oauth-v2-31" target="_blank">
OAuth 2.0 protocol</a> to see a complete list of error codes.

-----
> [back to top](#top)

-----
