# PCRE2 Package

Package: `libpcre2/libpcre2`

Base library: PCRE2

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpcre2
```

The package requires PCRE2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libpcre2\Libpcre2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libpcre2 = $runtime->load(Libpcre2::class);

// Compile a PCRE2 pattern (8-bit / UTF-8 API)
$errorCode   = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$errorOffset = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$re = $libpcre2->pcre2_compile_8('\\d+', -1, 0, $errorCode, $errorOffset, null);
if (is_null($re)) {
    throw new \RuntimeException('pcre2_compile_8 failed at offset ' . $errorOffset[0]);
}

// Match against a subject string
$matchData = $libpcre2->pcre2_match_data_create_from_pattern_8($re, null);
$rc = $libpcre2->pcre2_match_8($re, '42 items', 8, 0, 0, $matchData, null);
echo "Match count: {$rc}\n"; // 1 on success

$libpcre2->pcre2_match_data_free_8($matchData);
$libpcre2->pcre2_code_free_8($re);
```

This snippet is printed when `pnl install libpcre2` finishes — it comes from the package's `examples` field in `pnlx.json`.
