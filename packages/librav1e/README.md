# rav1e Package

Package: `librav1e/librav1e`

Base library: rav1e

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/librav1e
```

The package requires the rav1e headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Librav1e\Librav1e;

// rav1e_version_short() returns the rav1e AV1 encoder version string.
echo Librav1e::rav1e_version_short() . PHP_EOL;
```

This snippet is printed when `pnl install librav1e` finishes — it comes from the
package's `examples` field in `pnlx.json`.
