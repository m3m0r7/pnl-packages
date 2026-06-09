# libjpeg-turbo Package

Package: `libjpeg/libjpeg`

Base library: libjpeg-turbo

License: IJG

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libjpeg
```

The package requires libjpeg-turbo headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libjpeg` finishes — it comes from the package's `examples` field in `pnlx.json`.
