# liblz4/liblz4 examples

```php
use Pnlx\Liblz4\Liblz4;

$liblz4 = new Liblz4();

// Compress and decompress a string with LZ4.
$src = 'Hello, LZ4 compression!';
$srcSize = strlen($src);
$maxDst = $liblz4->LZ4_compressBound($srcSize); // returns int
$compressed = str_repeat("\0", $maxDst);
$compSize = $liblz4->LZ4_compress_default($src, $compressed, $srcSize, $maxDst);
$decompressed = str_repeat("\0", $srcSize);
$liblz4->LZ4_decompress_safe($compressed, $decompressed, $compSize, $srcSize);
echo $decompressed . PHP_EOL; // "Hello, LZ4 compression!"
```
