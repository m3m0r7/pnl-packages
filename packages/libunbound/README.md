# Unbound Package

Package: `libunbound/libunbound`

Base library: Unbound

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libunbound
```

The package requires the Unbound headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libunbound\Libunbound;

// ub_version() returns the linked libunbound version string.
echo Libunbound::ub_version() . PHP_EOL;
```

This snippet is printed when `pnl install libunbound` finishes — it comes from the
package's `examples` field in `pnlx.json`.
