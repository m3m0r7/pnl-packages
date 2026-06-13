# libxslt/libxslt examples

```php
use Pnlx\Libxslt\Libxslt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libxslt = $runtime->load(Libxslt::class);

// Allocate an empty stylesheet and release it again.
$sheet = $libxslt->xsltNewStylesheet();
$libxslt->xsltFreeStylesheet($sheet);
$libxslt->xsltCleanupGlobals();

// Explore further: xsltParseStylesheetFile(), xsltApplyStylesheet(),
// xsltSaveResultToString(), xsltFreeStylesheet(), ...
```
