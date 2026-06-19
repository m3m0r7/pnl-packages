# libjpeg/libjpeg examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libjpeg\Libjpeg;

// jpeg_quality_scaling() maps a 0-100 quality value onto libjpeg's internal
// scaling factor without needing a compression/decompression struct.
$scaled = Libjpeg::jpeg_quality_scaling(75); // returns int
echo 'libjpeg quality scaling for 75: ' . $scaled . PHP_EOL;
// Main entry points to explore: jpeg_CreateCompress / jpeg_CreateDecompress,
// jpeg_stdio_dest / jpeg_stdio_src, jpeg_start_compress, jpeg_finish_compress.
```
