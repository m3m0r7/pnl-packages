# Z3 Package

Package: `libz3/libz3`

Base library: Z3 (SMT solver)

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libz3
```

The package requires the Z3 headers and shared library to be available through
the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libz3\Libz3;

echo Libz3::Z3_get_full_version() . PHP_EOL;
```

This snippet is printed when `pnl install libz3` finishes — it comes from the
package's `examples` field in `pnlx.json`.
