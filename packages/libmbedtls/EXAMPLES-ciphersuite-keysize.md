# libmbedtls/libmbedtls ciphersuite key size

Resolve a ciphersuite descriptor by name with `mbedtls_ssl_ciphersuite_from_string()`, then read its symmetric key size with `mbedtls_ssl_ciphersuite_get_cipher_key_bitlen()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmbedtls\Libmbedtls;

// Resolve a ciphersuite descriptor by name, then read its symmetric key size.
$name = 'TLS-ECDHE-RSA-WITH-AES-256-GCM-SHA384';

$info = Libmbedtls::mbedtlsSslCiphersuiteFromString($name);
if ($info === null) {
    throw new \RuntimeException("unknown ciphersuite: {$name}");
}

$bits = Libmbedtls::mbedtlsSslCiphersuiteGetCipherKeyBitlen($info);
echo "{$name} cipher key: " . (is_object($bits) ? $bits->toInt() : $bits) . " bits" . PHP_EOL;
```
