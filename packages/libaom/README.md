# libaom AV1 Package

Package: `libaom/libaom`

Base library: libaom AV1

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libaom
```

The package requires the libaom AV1 headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libaom\Libaom;

// aom_codec_version_str() returns the libaom AV1 codec version string.
echo Libaom::aom_codec_version_str() . PHP_EOL;
```

This snippet is printed when `pnl install libaom` finishes — it comes from the
package's `examples` field in `pnlx.json`.
