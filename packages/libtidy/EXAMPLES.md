# libtidy/libtidy examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtidy\Libtidy;

use const Pnlx\Libtidy\TidyShowWarnings;
use const Pnlx\Libtidy\TidyXhtmlOut;

// Create a Tidy document, clean and repair an HTML string, then release.
// The TidyOptionId values are generated constants — their numeric values differ
// between libtidy builds, so never hard-code them.
$doc = Libtidy::tidyCreate();
Libtidy::tidyOptSetBool($doc, TidyXhtmlOut, 1);
Libtidy::tidyOptSetBool($doc, TidyShowWarnings, 0);
Libtidy::tidyParseString($doc, '<html><body><p>Hello<br>World</p></body></html>');
Libtidy::tidyCleanAndRepair($doc);
// Retrieve output via tidySaveBuffer; see tidybuffio.h for TidyBuffer helpers.
Libtidy::tidyRelease($doc);
```
