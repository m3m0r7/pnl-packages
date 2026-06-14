# libicu/libicu examples

```php
use Pnlx\Libicu\Libicu;

// Query the ICU library version
$verBuf = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
Libicu::u_getVersion($verBuf);
echo "ICU version: " . $verBuf[0] . "." . $verBuf[1] . "\n";

// Normalize a Unicode string to NFC using unorm2
// $norm = Libicu::unorm2_getNFCInstance($error);
// Libicu::unorm2_normalize($norm, $src, -1, $dest, $destCapacity, $error);
```
