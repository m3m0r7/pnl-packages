# libzstd/libzstd examples

```php
use Pnlx\Libzstd\Libzstd;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libzstd = $runtime->load(Libzstd::class);

// ZSTD_versionString() returns the library version, e.g. "1.5.6".
$version = $libzstd->ZSTD_versionString();
echo "Zstandard version: $version\n";

// ZSTD_compressBound(srcSize) returns the worst-case compressed size.
$bound = $libzstd->ZSTD_compressBound(1024);
echo "Max compressed size for 1024 bytes: $bound\n";

// Explore further: ZSTD_compress(), ZSTD_decompress(),
// ZSTD_createCCtx(), ZSTD_compressStream2(), ...
```
