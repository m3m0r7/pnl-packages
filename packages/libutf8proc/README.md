# utf8proc Package

Package: `libutf8proc/libutf8proc`

Base library: utf8proc

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libutf8proc
```

The package requires utf8proc headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libutf8proc` finishes — it comes from the package's `examples` field in `pnlx.json`.
