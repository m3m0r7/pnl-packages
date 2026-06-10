# libjpeg/libjpeg examples

```php
use Pnlx\Libjpeg\Libjpeg;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libjpeg = $runtime->load(Libjpeg::class);

// Query the compile-time library version (e.g. 80 for libjpeg v8).
$version = $libjpeg->jpeg_lib_version(); // returns int
echo 'libjpeg version: ' . $version . PHP_EOL;
// Main entry points to explore: jpeg_CreateCompress / jpeg_CreateDecompress,
// jpeg_stdio_dest / jpeg_stdio_src, jpeg_start_compress, jpeg_finish_compress.
```
