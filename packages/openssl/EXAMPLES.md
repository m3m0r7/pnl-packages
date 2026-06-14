# openssl/openssl examples

```php
use Pnlx\Openssl\Openssl;

// OpenSSL_version(0) returns the full version string (OPENSSL_VERSION == 0).
$version = Openssl::OpenSSL_version(0);
echo "OpenSSL: $version\n";

// Explore further: EVP_MD_CTX_new(), EVP_DigestInit_ex(),
// EVP_DigestUpdate(), EVP_DigestFinal_ex(), EVP_MD_CTX_free(), ...
```
