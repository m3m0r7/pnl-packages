# xxHash Package

Package: `libxxhash/libxxhash`

Base library: xxHash

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libxxhash
```

The package requires xxHash headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libxxhash\Libxxhash;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libxxhash = $runtime->load(Libxxhash::class);

// XXH_versionNumber() returns version as (major*100*100 + minor*100 + patch).
$ver = $libxxhash->XXH_versionNumber();
echo sprintf("xxHash %d.%d.%d\n",
    intdiv($ver, 10000), intdiv($ver % 10000, 100), $ver % 100);

// Explore further: XXH32(), XXH64(), XXH3_64bits(), XXH3_128bits(), ...
```

This snippet is printed when `pnl install libxxhash` finishes — it comes from the package's `examples` field in `pnlx.json`.
