# GNU Libtasn1 Package

Package: `libtasn1/libtasn1`

Base library: GNU Libtasn1

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libtasn1
```

The package requires the GNU Libtasn1 headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libtasn1\Libtasn1;

// asn1_check_version(null) returns the runtime Libtasn1 version string.
echo Libtasn1::asn1_check_version(null) . PHP_EOL;
```

This snippet is printed when `pnl install libtasn1` finishes — it comes from the
package's `examples` field in `pnlx.json`.
