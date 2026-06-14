# libdeflate/libdeflate examples

```php
use Pnlx\Libdeflate\Libdeflate;

// Allocate a compressor at level 6, then free it.
$compressor = Libdeflate::libdeflate_alloc_compressor(6);
Libdeflate::libdeflate_free_compressor($compressor);

// Explore further: libdeflate_deflate_compress(), libdeflate_gzip_compress(),
// libdeflate_alloc_decompressor(), libdeflate_zlib_decompress(), ...
```
