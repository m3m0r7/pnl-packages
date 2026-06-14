# libmbedtls/libmbedtls examples

```php
use Pnlx\Libmbedtls\Libmbedtls;

$libmbedtls = new Libmbedtls();

// Compute an SHA-256 digest using the Mbed TLS MD (message digest) API.
$ctx = $libmbedtls->mbedtls_md_info_from_type(6); // MBEDTLS_MD_SHA256 = 6
$mdCtx = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
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
