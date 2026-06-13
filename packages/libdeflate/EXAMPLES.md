# libdeflate/libdeflate examples

```php
use Pnlx\Libdeflate\Libdeflate;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libdeflate = $runtime->load(Libdeflate::class);

// Allocate a compressor at level 6, then free it.
$compressor = $libdeflate->libdeflate_alloc_compressor(6);
$libdeflate->libdeflate_free_compressor($compressor);

// Explore further: libdeflate_deflate_compress(), libdeflate_gzip_compress(),
// libdeflate_alloc_decompressor(), libdeflate_zlib_decompress(), ...
```
