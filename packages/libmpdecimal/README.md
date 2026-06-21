# mpdecimal Package

Package: `libmpdecimal/libmpdecimal`

Base library: mpdecimal

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmpdecimal
```

The package requires the mpdecimal headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmpdecimal\Libmpdecimal;

// mpd_version() returns the libmpdec version string.
echo Libmpdecimal::mpd_version() . PHP_EOL;
```

This snippet is printed when `pnl install libmpdecimal` finishes — it comes from the
package's `examples` field in `pnlx.json`.
