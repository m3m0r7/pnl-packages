# libsodium Package

Package: `libsodium/libsodium`

Base library: libsodium

License: ISC

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsodium
```

The package requires libsodium headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsodium\Libsodium;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsodium = $runtime->load(Libsodium::class);

// Initialise the library (must be called once before any crypto operation).
$libsodium->sodium_init();

// Print the library version string.
$version = $libsodium->sodium_version_string();
echo $version . PHP_EOL;

// Key and nonce size constants are returned as plain integers.
$keyBytes   = $libsodium->crypto_secretbox_keybytes();
$nonceBytes = $libsodium->crypto_secretbox_noncebytes();
echo "secretbox key={$keyBytes} nonce={$nonceBytes}" . PHP_EOL;
// Use $libsodium->crypto_secretbox_easy(...) for authenticated encryption.
```

This snippet is printed when `pnl install libsodium` finishes — it comes from the package's `examples` field in `pnlx.json`.
