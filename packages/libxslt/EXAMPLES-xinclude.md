# libxslt XInclude default flag

`xsltGetXIncludeDefault()` and `xsltSetXIncludeDefault()` read and toggle the global flag that controls whether XInclude processing runs during transforms.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libxslt\Libxslt;

// Read, toggle, and restore the global default XInclude processing flag.
$original = Libxslt::xsltGetXIncludeDefault();
echo "default xinclude: " . (is_object($original) ? $original->toInt() : $original) . "\n";

Libxslt::xsltSetXIncludeDefault(1);
$enabled = Libxslt::xsltGetXIncludeDefault();
echo "after enabling: " . (is_object($enabled) ? $enabled->toInt() : $enabled) . "\n";

Libxslt::xsltSetXIncludeDefault(is_object($original) ? $original->toInt() : $original);
$restored = Libxslt::xsltGetXIncludeDefault();
echo "restored: " . (is_object($restored) ? $restored->toInt() : $restored) . "\n";
```
