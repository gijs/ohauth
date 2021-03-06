## ohauth

A most-of-the-way OAuth 1.0 client implementation in Javascript. Meant to be
an improvement over the [default linked one](http://oauth.googlecode.com/svn/code/javascript/)
because this uses idiomatic Javascript.

This includes [Paul Johnston's venerable implementation of SHA1](http://pajhome.org.uk/crypt/md5/).

If you use this on a server [different from the one authenticated against](http://en.wikipedia.org/wiki/Same_origin_policy),
you'll need to [enable](http://enable-cors.org/) and use [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing)
for cross-origin resources. CORS is not available in IE before version IE10.

```js
// generates an oauth-friendly timestamp
ohauth.timestamp();

// generates an oauth-friendly nonce
ohauth.nonce();

// generate a signature for an oauth request
ohauth.signature({
    oauth_consumer_key: '...',
    oauth_signature_method: '...',
    oauth_timestamp: '...',
    oauth_nonce: '...'
});

// make an oauth request.
ohauth.xhr(method, url, auth, data, options, callback);

// options can be a header like
{ header: { 'Content-Type': 'text/xml' } }

ohauth.xhr('POST', url, o, null, {}, function(xhr) {
    // xmlhttprequest object
});

// generate a querystring from an object
ohauth.qsString({ foo: 'bar' });
// foo=bar

// generate an object from a querystring
ohauth.stringQs('foo=bar');
// { foo: 'bar' }
```
