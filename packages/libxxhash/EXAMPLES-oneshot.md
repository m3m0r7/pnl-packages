# libxxhash one-shot hashing

Compute XXH32, XXH64, and XXH3_64bits digests of a PHP string in a single call by passing the string as the buffer and its byte length.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libxxhash\Libxxhash;

// One-shot hashing: pass a PHP string directly as the buffer and its byte length.
$data = "The quick brown fox jumps over the lazy dog";
$len  = strlen($data);

$h32 = Libxxhash::XXH32($data, $len, 0);
$h64 = Libxxhash::XXH64($data, $len, 0);
$h3  = Libxxhash::XXH3_64bits($data, $len);

$asInt = fn($x) => is_object($x) ? $x->toInt() : $x;

echo sprintf("XXH32       : 0x%08x\n", $asInt($h32) & 0xffffffff);
echo sprintf("XXH64       : 0x%016x\n", $asInt($h64));
echo sprintf("XXH3_64bits : 0x%016x\n", $asInt($h3));
```
