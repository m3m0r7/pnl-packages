# CFITSIO Package

Package: `libcfitsio/libcfitsio`

Base library: CFITSIO

License: cfitsio

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcfitsio
```

The package requires the CFITSIO headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libcfitsio\Libcfitsio;

// ffvers() writes the CFITSIO version into its float out-parameter.
$version = 0.0;
Libcfitsio::ffvers($version);
printf("cfitsio %.3f\n", $version);
```

This snippet is printed when `pnl install libcfitsio` finishes — it comes from the
package's `examples` field in `pnlx.json`.
