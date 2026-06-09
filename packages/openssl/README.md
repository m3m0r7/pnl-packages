# OpenSSL Package

Package: `openssl/openssl`

Base library: OpenSSL

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/openssl
```

The package requires OpenSSL headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Openssl\Openssl;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$openssl = $runtime->load(Openssl::class);

// OpenSSL_version(0) returns the full version string (OPENSSL_VERSION == 0).
$version = $openssl->OpenSSL_version(0);
echo "OpenSSL: $version\n";

// Explore further: EVP_MD_CTX_new(), EVP_DigestInit_ex(),
// EVP_DigestUpdate(), EVP_DigestFinal_ex(), EVP_MD_CTX_free(), ...
```

This snippet is printed when `pnl install openssl` finishes — it comes from the package's `examples` field in `pnlx.json`.
