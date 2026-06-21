# Graphite2 Package

Package: `libgraphite2/libgraphite2`

Base library: Graphite2

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgraphite2
```

The package requires the Graphite2 headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libgraphite2\Libgraphite2;

// gr_engine_version() writes major/minor/bugfix into its out-parameters.
$major = null; $minor = null; $bugfix = null;
Libgraphite2::gr_engine_version($major, $minor, $bugfix);
echo "graphite2 {$major}.{$minor}.{$bugfix}" . PHP_EOL;
```

This snippet is printed when `pnl install libgraphite2` finishes — it comes from the
package's `examples` field in `pnlx.json`.
