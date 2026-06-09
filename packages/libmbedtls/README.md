# Mbed TLS Package

Package: `libmbedtls/libmbedtls`

Base library: Mbed TLS

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmbedtls
```

The package requires Mbed TLS headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmbedtls\Libmbedtls;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libmbedtls = $runtime->load(Libmbedtls::class);

// Compute an SHA-256 digest using the Mbed TLS MD (message digest) API.
$ctx = $libmbedtls->mbedtls_md_info_from_type(6); // MBEDTLS_MD_SHA256 = 6
$mdCtx = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libmbedtls->mbedtls_md_init($mdCtx);
$libmbedtls->mbedtls_md_setup($mdCtx, $ctx, 0);
$libmbedtls->mbedtls_md_starts($mdCtx);
$msg = 'hello';
$libmbedtls->mbedtls_md_update($mdCtx, $msg, strlen($msg));
$out = str_repeat("\0", 32);
$libmbedtls->mbedtls_md_finish($mdCtx, $out);
echo bin2hex($out) . PHP_EOL; // SHA-256 of "hello"
$libmbedtls->mbedtls_md_free($mdCtx);
```

This snippet is printed when `pnl install libmbedtls` finishes — it comes from the package's `examples` field in `pnlx.json`.
