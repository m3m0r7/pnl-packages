# FreeTDS Package

Package: `libfreetds/libfreetds`

Base library: FreeTDS

License: LGPL-2.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libfreetds
```

The package requires the FreeTDS headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libfreetds\Libfreetds;

// dbversion() returns the FreeTDS DB-Library version string.
echo Libfreetds::dbversion() . PHP_EOL;
```

This snippet is printed when `pnl install libfreetds` finishes — it comes from the
package's `examples` field in `pnlx.json`.
