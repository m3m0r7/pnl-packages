# libksba Package

Package: `libksba/libksba`

Base library: libksba

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libksba
```

The package requires the libksba headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libksba\Libksba;

// ksba_check_version(null) returns the runtime libksba version string.
echo Libksba::ksba_check_version(null) . PHP_EOL;
```

This snippet is printed when `pnl install libksba` finishes — it comes from the
package's `examples` field in `pnlx.json`.
