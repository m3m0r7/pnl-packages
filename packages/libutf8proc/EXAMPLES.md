# libutf8proc/libutf8proc examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libutf8proc\Libutf8proc;

// Print the library version string.
echo Libutf8proc::utf8proc_version() . PHP_EOL;

// Look up the Unicode category name for a codepoint (e.g. U+0041 'A' -> Lu).
$category = Libutf8proc::utf8proc_category(0x0041); // returns int (enum)
$name = Libutf8proc::utf8proc_category_string(0x0041); // returns char*
echo "U+0041 category: {$name}" . PHP_EOL;

// Normalise a UTF-8 string to NFC (UTF8PROC_COMPOSE=1).
// $out = Libutf8proc::utf8proc_map($input, strlen($input), $outPtr, 1);
```
