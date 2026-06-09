# HTML Tidy Package

Package: `libtidy/libtidy`

Base library: HTML Tidy

License: W3C

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libtidy
```

The package requires HTML Tidy headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libtidy\Libtidy;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libtidy = $runtime->load(Libtidy::class);

// Create a Tidy document, clean and repair an HTML string, then release.
$doc = $libtidy->tidyCreate();
$libtidy->tidyOptSetBool($doc, 1 /* TidyXhtmlOut */, 1);
$libtidy->tidyOptSetBool($doc, 68 /* TidyShowWarnings */, 0);
$libtidy->tidyParseString($doc, '<html><body><p>Hello<br>World</p></body></html>');
$libtidy->tidyCleanAndRepair($doc);
// Retrieve output via tidySaveBuffer; see tidybuffio.h for TidyBuffer helpers.
$libtidy->tidyRelease($doc);
```

This snippet is printed when `pnl install libtidy` finishes — it comes from the package's `examples` field in `pnlx.json`.
