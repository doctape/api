# How To Sign Requests

## Simple Signing Scheme

A request is signed over the _Application Secret_ and a _Target_ using the HMAC SHA1 signing function.

For access to resources concerning a specific document, the _Target_ is the ID of the document. For everything else (currently only upload), the _Target_ is the e-mail address of the user you want to target.

**CAUTION: Make sure that your Application Secret is always kept private!**

To retrieve the _Signature_, calculate the hexadecimal representation of the SHA1 HMAC digest using the _Application Secret_ as the key and the _Target_ as the message.

When performing a request, pass the _Signature_ as the query parameter `auth` along with the rest of the query parameters.

## Advanced Signing Scheme

A request is signed over a set of parameters `P` (it is assumed that parameter keys and values are both strings) as well as your application secret `S`. Which parameters assemble `P` for a specific request is mentioned in the description for the matching endpoint.

**CAUTION: Make sure that your application secret is always kept private!**

As the input to the signing function a _Parameter String_ has to be built from `P` in the same way as the key-value query part of an URI (see the [W3C HTML Form Recommendation](http://www.w3.org/TR/REC-html40/interact/forms.html#form-content-type) for reference), with the additional requirement that the order of the key-value pairs is determined by the lexicographical order of the parameter keys.

Below you find a reference implementation of this process in the JavaScript language, which assumes that its input `params` is a key-value object of parameters.

```
var encodeParams = function (params) {
  var encode = function (k) { return encodeURIComponent(k) + '=' + encodeURIComponent(params[k]); };
  return Object.keys(params)
               .sort()
               .map(encode)
               .join('&');
};
```

After retrieving the _Parameter String_ you obtain the key `K` for the signature by calculating the hexadecimal representation of the HMAC SHA1 digest using the _Parameter String_ as the message and the app secret `S` as the secret.

The final _Signature_ is then, again, created by calculating the hexadecimal representation of the HMAC SHA1 digest using the _Parameter String_ as the message and `K` as the secret. In pseudocode:

```
paramstr  = encodeParams(params)
signature = HMACSHA1HEX(message: paramstr, key: HMACSHA1HEX(message: paramstr, key: S))
```

When performing a request, pass the _Signature_ as the query parameter `multiauth` along with the rest of the query parameters.