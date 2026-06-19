# libidn2/libidn2 examples

```php
use Pnlx\Libidn2\Libidn2;

// Check library version
$version = Libidn2::idn2_check_version('2.0.0');
echo "libidn2 version >= 2.0.0: " . ($version !== null ? $version : 'no') . "\n";

// Convert an internationalized domain name to ACE (ASCII-compatible encoding).
// The `uint8_t **lookupname` out-parameter is a C-string out: pass a variable by
// reference and it is written back as a PHP string (the allocated buffer is read
// and copied for you).
$ace = null;
$rc = Libidn2::idn2_lookup_u8("www.b\u{00fc}cher.example", $ace, 0);
if ($rc === 0) {
    echo "ACE label: $ace\n"; // www.xn--bcher-kva.example
}
```
