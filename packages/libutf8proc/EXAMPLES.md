# libutf8proc/libutf8proc examples

```php
use Pnlx\Libutf8proc\Libutf8proc;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libutf8proc = $runtime->load(Libutf8proc::class);

// Print the library version string.
echo $libutf8proc->utf8proc_version() . PHP_EOL;

// Look up the Unicode category name for a codepoint (e.g. U+0041 'A' -> Lu).
$category = $libutf8proc->utf8proc_category(0x0041); // returns int (enum)
$name = $libutf8proc->utf8proc_category_string(0x0041); // returns char*
echo "U+0041 category: {$name}" . PHP_EOL;

// Normalise a UTF-8 string to NFC (UTF8PROC_COMPOSE=1).
// $out = $libutf8proc->utf8proc_map($input, strlen($input), $outPtr, 1);
```
