# libsodium/libsodium examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsodium\Libsodium;

// Initialise the library (must be called once before any crypto operation).
Libsodium::sodium_init();

// Print the library version string.
$version = Libsodium::sodium_version_string();
echo $version . PHP_EOL;

// Key and nonce size constants come back as Stringable integer wrappers.
$keyBytes   = Libsodium::crypto_secretbox_keybytes();
$nonceBytes = Libsodium::crypto_secretbox_noncebytes();
echo "secretbox key={$keyBytes} nonce={$nonceBytes}" . PHP_EOL;
// Use Libsodium::crypto_secretbox_easy(...) for authenticated encryption.
```
