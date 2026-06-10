# libicu/libicu examples

```php
use Pnlx\Libicu\Libicu;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libicu = $runtime->load(Libicu::class);

// Query the ICU library version
$verBuf = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$libicu->u_getVersion($verBuf);
echo "ICU version: " . $verBuf[0] . "." . $verBuf[1] . "\n";

// Normalize a Unicode string to NFC using unorm2
// $norm = $libicu->unorm2_getNFCInstance($error);
// $libicu->unorm2_normalize($norm, $src, -1, $dest, $destCapacity, $error);
```
