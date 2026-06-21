# NSS Package

Package: `libnss/libnss`

Base library: NSS

License: MPL-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnss
```

The package requires the NSS headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libnss\Libnss;

// NSS_GetVersion() returns the NSS library version string.
echo Libnss::NSS_GetVersion() . PHP_EOL;
```

This snippet is printed when `pnl install libnss` finishes — it comes from the
package's `examples` field in `pnlx.json`.
