# libgcrypt digest algorithm metadata

Resolve a hash digest name to its algorithm id, look the name back up, and read its output length.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgcrypt\Libgcrypt;

// gcry_md_map_name() resolves a digest name to its algorithm id,
// and gcry_md_algo_name() is the inverse lookup.
$algo = Libgcrypt::gcry_md_map_name('SHA256');
$algoId = is_object($algo) ? $algo->toInt() : $algo;
echo "SHA256 algorithm id: {$algoId}" . PHP_EOL;

$name = Libgcrypt::gcry_md_algo_name($algoId);
echo "algorithm name: " . (string)$name . PHP_EOL;

// gcry_md_get_algo_dlen() reports the digest output length in bytes.
$dlen = Libgcrypt::gcry_md_get_algo_dlen($algoId);
echo "digest length: " . (is_object($dlen) ? $dlen->toInt() : $dlen) . " bytes" . PHP_EOL;
```
