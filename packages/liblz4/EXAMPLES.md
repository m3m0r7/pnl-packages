# liblz4/liblz4 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblz4\Liblz4;

// Compress and decompress a string with LZ4.
$src = 'Hello, LZ4 compression!';
$srcSize = strlen($src);
$maxDst = Liblz4::LZ4_compressBound($srcSize)->toInt(); // returns int (Int_->toInt() for str_repeat)
$compressed = str_repeat("\0", $maxDst);
$compSize = Liblz4::LZ4_compress_default($src, $compressed, $srcSize, $maxDst);
$decompressed = str_repeat("\0", $srcSize);
Liblz4::LZ4_decompress_safe($compressed, $decompressed, $compSize, $srcSize);
echo $decompressed . PHP_EOL; // "Hello, LZ4 compression!"
```
