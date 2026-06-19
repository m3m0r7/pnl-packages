# libxslt/libxslt examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libxslt\Libxslt;

// Allocate an empty stylesheet and release it again.
$sheet = Libxslt::xsltNewStylesheet();
Libxslt::xsltFreeStylesheet($sheet);
Libxslt::xsltCleanupGlobals();

// Explore further: xsltParseStylesheetFile(), xsltApplyStylesheet(),
// xsltSaveResultToString(), xsltFreeStylesheet(), ...
```
