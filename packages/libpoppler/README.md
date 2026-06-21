# Poppler Package

Package: `libpoppler/libpoppler`

Base library: Poppler

License: GPL-2.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpoppler
```

The package requires the Poppler headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libpoppler\Libpoppler;

// poppler_get_version() returns the Poppler library version string.
echo Libpoppler::poppler_get_version() . PHP_EOL;
```

This snippet is printed when `pnl install libpoppler` finishes — it comes from the
package's `examples` field in `pnlx.json`.
