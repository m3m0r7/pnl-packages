# libtidy/libtidy examples

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
