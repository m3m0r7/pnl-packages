# libmbedtls/libmbedtls examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmbedtls\Libmbedtls;

// Look up a TLS ciphersuite by name, then resolve its id back to a name.
// These functions are part of the Mbed TLS SSL/TLS layer shipped in libmbedtls,
// and need no context/struct allocation.
$name = 'TLS-ECDHE-RSA-WITH-AES-128-GCM-SHA256';

$id = (int) (string) Libmbedtls::mbedtlsSslGetCiphersuiteId($name);
echo "ciphersuite id: {$id}" . PHP_EOL;

$resolved = (string) Libmbedtls::mbedtlsSslGetCiphersuiteName($id);
echo "ciphersuite name: {$resolved}" . PHP_EOL;
```
