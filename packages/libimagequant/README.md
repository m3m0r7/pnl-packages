# libimagequant Package

Package: `libimagequant/libimagequant`

Base library: libimagequant

License: GPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libimagequant
```

The package requires the libimagequant headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libimagequant\Libimagequant;

// liq_version() returns the libimagequant version encoded as MMmmpp (e.g. 40001).
echo Libimagequant::liq_version()->toInt() . PHP_EOL;
```

This snippet is printed when `pnl install libimagequant` finishes — it comes from the
package's `examples` field in `pnlx.json`.
