# SVT-AV1 Package

Package: `libsvtav1/libsvtav1`

Base library: SVT-AV1

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsvtav1
```

The package requires the SVT-AV1 headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsvtav1\Libsvtav1;

// svt_av1_get_version() returns the SVT-AV1 encoder version string.
echo Libsvtav1::svt_av1_get_version() . PHP_EOL;
```

This snippet is printed when `pnl install libsvtav1` finishes — it comes from the
package's `examples` field in `pnlx.json`.
