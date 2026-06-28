# libutf8proc/libutf8proc case mapping and character metrics

`utf8proc_unicode_version()` reports the backing Unicode standard, while `utf8proc_toupper()`, `utf8proc_tolower()`, and `utf8proc_charwidth()` are pure per-codepoint transforms returning scalars.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libutf8proc\Libutf8proc;

// utf8proc_unicode_version() reports the Unicode standard version backing the tables.
echo "Unicode version: " . (string)Libutf8proc::utf8proc_unicode_version() . PHP_EOL;

// utf8proc_toupper() / utf8proc_tolower() are pure codepoint case mappings.
$up = Libutf8proc::utf8proc_toupper(0x0061); // 'a' -> 'A'
$upVal = is_object($up) ? $up->toInt() : $up;
echo "toupper(U+0061) = U+" . sprintf('%04X', $upVal) . PHP_EOL;

$lo = Libutf8proc::utf8proc_tolower(0x0041); // 'A' -> 'a'
$loVal = is_object($lo) ? $lo->toInt() : $lo;
echo "tolower(U+0041) = U+" . sprintf('%04X', $loVal) . PHP_EOL;

// utf8proc_charwidth() returns the column width of a codepoint when printed.
$w = Libutf8proc::utf8proc_charwidth(0x4E00); // CJK ideograph -> width 2
$wVal = is_object($w) ? $w->toInt() : $w;
echo "charwidth(U+4E00) = " . $wVal . PHP_EOL;
```
