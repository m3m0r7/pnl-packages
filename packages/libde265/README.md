# libde265 Package

Package: `libde265/libde265`

Base library: libde265

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libde265
```

The package requires the libde265 headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libde265\Libde265;

// de265_get_version() returns the libde265 HEVC decoder version string.
echo Libde265::de265_get_version() . PHP_EOL;
```

This snippet is printed when `pnl install libde265` finishes — it comes from the
package's `examples` field in `pnlx.json`.
