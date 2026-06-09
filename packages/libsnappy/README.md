# Snappy Package

Package: `libsnappy/libsnappy`

Base library: Snappy

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsnappy
```

The package requires Snappy headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsnappy\Libsnappy;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsnappy = $runtime->load(Libsnappy::class);

$input    = 'Hello, Snappy compression!';
$inputLen = strlen($input);

// Allocate output buffer sized to the worst-case compressed length
$maxLen      = $libsnappy->snappy_max_compressed_length($inputLen);
$compressed  = str_repeat("\0", $maxLen);
$compressedLen = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$compressedLen[0] = $maxLen;

$rc = $libsnappy->snappy_compress($input, $inputLen, $compressed, $compressedLen);
if ($rc !== 0) { // SNAPPY_OK = 0
    throw new \RuntimeException("snappy_compress failed: {$rc}");
}
echo "Compressed {$inputLen} -> {$compressedLen[0]} bytes\n";

// Decompress back
$uncompressedLen = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$libsnappy->snappy_uncompressed_length($compressed, $compressedLen[0], $uncompressedLen);
$output = str_repeat("\0", $uncompressedLen[0]);
$libsnappy->snappy_uncompress($compressed, $compressedLen[0], $output, $uncompressedLen);
echo $output . "\n";
```

This snippet is printed when `pnl install libsnappy` finishes — it comes from the package's `examples` field in `pnlx.json`.
