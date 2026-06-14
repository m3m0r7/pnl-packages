# libtidy/libtidy examples

```php
use Pnlx\Libtidy\Libtidy;

// Create a Tidy document, clean and repair an HTML string, then release.
$doc = Libtidy::tidyCreate();
Libtidy::tidyOptSetBool($doc, 1 /* TidyXhtmlOut */, 1);
Libtidy::tidyOptSetBool($doc, 68 /* TidyShowWarnings */, 0);
Libtidy::tidyParseString($doc, '<html><body><p>Hello<br>World</p></body></html>');
Libtidy::tidyCleanAndRepair($doc);
// Retrieve output via tidySaveBuffer; see tidybuffio.h for TidyBuffer helpers.
Libtidy::tidyRelease($doc);
```
