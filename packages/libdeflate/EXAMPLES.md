# libdeflate/libdeflate examples

```php
use Pnlx\Libdeflate\Libdeflate;

$libdeflate = new Libdeflate();

// Allocate a compressor at level 6, then free it.
$compressor = $libdeflate->libdeflate_alloc_compressor(6);
$libdeflate->libdeflate_free_compressor($compressor);

// Explore further: libdeflate_deflate_compress(), libdeflate_gzip_compress(),
// libdeflate_alloc_decompressor(), libdeflate_zlib_decompress(), ...
```
