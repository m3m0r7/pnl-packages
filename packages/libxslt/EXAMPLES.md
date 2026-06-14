# libxslt/libxslt examples

```php
use Pnlx\Libxslt\Libxslt;

$libxslt = new Libxslt();

// Allocate an empty stylesheet and release it again.
$sheet = $libxslt->xsltNewStylesheet();
$libxslt->xsltFreeStylesheet($sheet);
$libxslt->xsltCleanupGlobals();

// Explore further: xsltParseStylesheetFile(), xsltApplyStylesheet(),
// xsltSaveResultToString(), xsltFreeStylesheet(), ...
```
