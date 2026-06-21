# Capstone Package

Package: `libcapstone/libcapstone`

Base library: Capstone

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcapstone
```

The package requires the Capstone headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libcapstone\Libcapstone;

// cs_version() writes major/minor into its int out-parameters (pass plain
// variables by reference) and returns the combined version number.
$major = null;
$minor = null;
Libcapstone::cs_version($major, $minor);
echo "capstone {$major}.{$minor}" . PHP_EOL;
```

This snippet is printed when `pnl install libcapstone` finishes — it comes from the
package's `examples` field in `pnlx.json`.
