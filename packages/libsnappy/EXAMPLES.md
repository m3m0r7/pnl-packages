# libsnappy/libsnappy examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsnappy\Libsnappy;

// `size_t`/`snappy_status` returns may arrive wrapped (64-bit) or as a plain int
// depending on the platform — normalise with a tiny helper.
$asInt = static fn ($v) => is_object($v) ? $v->toInt() : (int) $v;

$input    = str_repeat('Hello, Snappy! ', 8);
$inputLen = strlen($input);

// A writable `char *` buffer is a by-reference parameter: pass a pre-sized string
// (its length is the capacity) and the written bytes come back in the variable.
$maxLen        = $asInt(Libsnappy::snappy_max_compressed_length($inputLen));
$compressed    = str_repeat("\0", $maxLen);
$compressedLen = $maxLen; // size_t* in/out: starts as the capacity, set to the real length

if ($asInt(Libsnappy::snappy_compress($input, $inputLen, $compressed, $compressedLen)) !== 0) {
    throw new \RuntimeException('snappy_compress failed'); // SNAPPY_OK = 0
}
$compressed = substr($compressed, 0, $compressedLen); // trim to the real length
echo "Compressed {$inputLen} -> {$compressedLen} bytes\n";

// Decompress back
$uncompressedLen = 0;
Libsnappy::snappy_uncompressed_length($compressed, strlen($compressed), $uncompressedLen);
$output    = str_repeat("\0", $uncompressedLen);
$outputLen = $uncompressedLen;
Libsnappy::snappy_uncompress($compressed, strlen($compressed), $output, $outputLen);
echo substr($output, 0, $outputLen) . "\n";
```
