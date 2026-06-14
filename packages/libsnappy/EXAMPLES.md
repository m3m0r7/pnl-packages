# libsnappy/libsnappy examples

```php
use Pnlx\Libsnappy\Libsnappy;

$libsnappy = new Libsnappy();

$input    = 'Hello, Snappy compression!';
$inputLen = strlen($input);

// Allocate output buffer sized to the worst-case compressed length
$maxLen      = $libsnappy->snappy_max_compressed_length($inputLen);
$compressed  = str_repeat("\0", $maxLen);
$compressedLen = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$compressedLen[0] = $maxLen;

$rc = $libsnappy->snappy_compress($input, $inputLen, $compressed, $compressedLen);
if ($rc !== 0) { // SNAPPY_OK = 0
    throw new \RuntimeException("snappy_compress failed: {$rc}");
}
echo "Compressed {$inputLen} -> {$compressedLen[0]} bytes\n";

// Decompress back
$uncompressedLen = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$libsnappy->snappy_uncompressed_length($compressed, $compressedLen[0], $uncompressedLen);
$output = str_repeat("\0", $uncompressedLen[0]);
$libsnappy->snappy_uncompress($compressed, $compressedLen[0], $output, $uncompressedLen);
echo $output . "\n";
```
