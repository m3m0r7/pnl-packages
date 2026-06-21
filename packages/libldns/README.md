# ldns Package

Package: `libldns/libldns`

Base library: ldns

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libldns
```

The package requires the ldns headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libldns\Libldns;

// ldns_version() returns the linked ldns library version.
echo Libldns::ldns_version() . PHP_EOL;
```

This snippet is printed when `pnl install libldns` finishes — it comes from the
package's `examples` field in `pnlx.json`.
