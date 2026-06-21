# matio Package

Package: `libmatio/libmatio`

Base library: matio

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmatio
```

The package requires the matio headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmatio\Libmatio;

// Mat_GetLibraryVersion() writes major/minor/release into its out-parameters.
$major = null; $minor = null; $release = null;
Libmatio::Mat_GetLibraryVersion($major, $minor, $release);
echo "matio {$major}.{$minor}.{$release}" . PHP_EOL;
```

This snippet is printed when `pnl install libmatio` finishes — it comes from the
package's `examples` field in `pnlx.json`.
