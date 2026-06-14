# libidn2/libidn2 examples

```php
use Pnlx\Libidn2\Libidn2;
use function Pnlx\Util\is_null;

// Check library version
$version = Libidn2::idn2_check_version('2.0.0');
echo "libidn2 version >= 2.0.0: " . ($version !== null ? $version : 'no') . "\n";

// Convert an internationalized domain name to ACE (ASCII-compatible encoding)
$output = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = Libidn2::idn2_lookup_u8('www.b\u00fccher.example', $output, 0);
if ($rc === 0) {
    echo "ACE label: " . $output[0] . "\n";
    Libidn2::idn2_free($output[0]);
}
```
