# dav1d Package

Package: `libdav1d/libdav1d`

Base library: dav1d

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libdav1d
```

The package requires the dav1d headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libdav1d\Libdav1d;

// dav1d_version() returns the dav1d AV1 decoder version string.
echo Libdav1d::dav1d_version() . PHP_EOL;
```

This snippet is printed when `pnl install libdav1d` finishes — it comes from the
package's `examples` field in `pnlx.json`.
