# openssl/openssl examples

```php
use Pnlx\Openssl\Openssl;

// Build a TLS context and a fresh SSL object, then read the
// negotiated protocol version label via the libssl API.
$method = Openssl::TLS_method();
$ctx    = Openssl::SSL_CTX_new($method);
$ssl    = Openssl::SSL_new($ctx);

// SSL_get_version() returns a const char* (e.g. "TLS").
$version = (string) Openssl::SSL_get_version($ssl);
echo "SSL protocol family: {$version}\n";

// Clean up the SSL object.
Openssl::SSL_free($ssl);

// Explore further: SSL_CTX_new(), SSL_connect(), SSL_read(),
// SSL_write(), SSL_shutdown(), SSL_CTX_free(), ...
```
</content>
