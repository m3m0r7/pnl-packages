# libsodium/libsodium examples

```php
use Pnlx\Libsodium\Libsodium;

$libsodium = new Libsodium();

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
