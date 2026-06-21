# HDF5 Package

Package: `libhdf5/libhdf5`

Base library: HDF5

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libhdf5
```

The package requires the HDF5 headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libhdf5\Libhdf5;

// H5get_libversion() writes major/minor/release into its out-parameters.
$major = null; $minor = null; $release = null;
Libhdf5::H5get_libversion($major, $minor, $release);
echo "hdf5 {$major}.{$minor}.{$release}" . PHP_EOL;
```

This snippet is printed when `pnl install libhdf5` finishes — it comes from the
package's `examples` field in `pnlx.json`.
