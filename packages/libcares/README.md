# c-ares Package

Package: `libcares/libcares`

Base library: c-ares

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcares
```

The package requires c-ares headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libcares\Libcares;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libcares = $runtime->load(Libcares::class);

// Initialise the c-ares library and print its version string
$rc = $libcares->ares_library_init(1); // ARES_LIB_INIT_ALL = 1
if ($rc !== 0) {
    throw new \RuntimeException("ares_library_init failed: {$rc}");
}

$versionNumber = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$versionStr    = $libcares->ares_version($versionNumber);
echo "c-ares version: {$versionStr}\n";

// Asynchronous DNS: $libcares->ares_init($channel) then $libcares->ares_gethostbyname(...)
$libcares->ares_library_cleanup();
```

This snippet is printed when `pnl install libcares` finishes — it comes from the package's `examples` field in `pnlx.json`.
