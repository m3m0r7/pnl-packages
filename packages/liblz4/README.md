# LZ4 Package

Package: `liblz4/liblz4`

Base library: LZ4

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liblz4
```

The package requires LZ4 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Liblz4\Liblz4;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$liblz4 = $runtime->load(Liblz4::class);

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

This snippet is printed when `pnl install liblz4` finishes — it comes from the package's `examples` field in `pnlx.json`.
