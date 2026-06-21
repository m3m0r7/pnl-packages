# zimg Package

Package: `libzimg/libzimg`

Base library: zimg

License: WTFPL

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libzimg
```

The package requires the zimg headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libzimg\Libzimg;

// zimg_get_version_info() writes major/minor/micro into its out-parameters.
$major = null; $minor = null; $micro = null;
Libzimg::zimg_get_version_info($major, $minor, $micro);
echo "zimg {$major}.{$minor}.{$micro}" . PHP_EOL;
```

This snippet is printed when `pnl install libzimg` finishes — it comes from the
package's `examples` field in `pnlx.json`.
