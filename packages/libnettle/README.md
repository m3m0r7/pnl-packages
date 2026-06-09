# Nettle Package

Package: `libnettle/libnettle`

Base library: Nettle

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnettle
```

The package requires Nettle headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libnettle\Libnettle;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnettle = $runtime->load(Libnettle::class);

// Query the library version
$major = $libnettle->nettle_version_major(); // returns int
$minor = $libnettle->nettle_version_minor(); // returns int
echo "Nettle version: $major.$minor\n";

// Compute a SHA-256 digest using the unprefixed algorithm functions
$ctx = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libnettle->sha256_init($ctx);
$libnettle->sha256_update($ctx, strlen('hello'), 'hello');
$digest = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libnettle->sha256_digest($ctx, 32, $digest);
```

This snippet is printed when `pnl install libnettle` finishes — it comes from the package's `examples` field in `pnlx.json`.
