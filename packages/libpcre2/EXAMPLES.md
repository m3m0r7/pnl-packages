# libpcre2/libpcre2 examples

```php
use Pnlx\Libpcre2\Libpcre2;
use function Pnlx\Util\is_null;

// Compile a PCRE2 pattern (8-bit / UTF-8 API)
$errorCode   = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$errorOffset = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$re = Libpcre2::pcre2_compile_8('\\d+', -1, 0, $errorCode, $errorOffset, null);
if (is_null($re)) {
    throw new \RuntimeException('pcre2_compile_8 failed at offset ' . $errorOffset[0]);
}

// Match against a subject string
$matchData = Libpcre2::pcre2_match_data_create_from_pattern_8($re, null);
$rc = Libpcre2::pcre2_match_8($re, '42 items', 8, 0, 0, $matchData, null);
echo "Match count: {$rc}\n"; // 1 on success

Libpcre2::pcre2_match_data_free_8($matchData);
Libpcre2::pcre2_code_free_8($re);
```
