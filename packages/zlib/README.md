# zlib Package

Package: `zlib/zlib`

Base library: zlib

License: Zlib

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/zlib
```

The package requires zlib headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Zlib\Zlib;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$zlib = $runtime->load(Zlib::class);

// zlibVersion() returns the library version string, e.g. "1.3.1".
$version = $zlib->zlibVersion();
echo "zlib version: $version\n";

// compressBound(sourceLen) returns the worst-case compressed size.
$bound = $zlib->compressBound(1024);
echo "Max compressed size for 1024 bytes: $bound\n";

// Explore further: compress2(), uncompress(), deflateInit(),
// deflate(), deflateEnd(), inflateInit(), inflate(), inflateEnd(), ...
```

This snippet is printed when `pnl install zlib` finishes — it comes from the package's `examples` field in `pnlx.json`.
