# libicu/libicu examples

```php
use Pnlx\Libicu\Libicu;

$libicu = new Libicu();

// Query the ICU library version
$verBuf = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$libicu->u_getVersion($verBuf);
echo "ICU version: " . $verBuf[0] . "." . $verBuf[1] . "\n";

// Normalize a Unicode string to NFC using unorm2
// $norm = $libicu->unorm2_getNFCInstance($error);
// $libicu->unorm2_normalize($norm, $src, -1, $dest, $destCapacity, $error);
```
