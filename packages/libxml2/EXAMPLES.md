# libxml2/libxml2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libxml2\Libxml2;
use function Pnlx\Util\is_null;

// xmlReadMemory() parses an XML document held in a string buffer.
$xml = "<root><item>hello</item></root>";
$doc = Libxml2::xmlReadMemory($xml, strlen($xml), "doc.xml", null, 0);
if (is_null($doc)) {
    echo "Parse failed\n";
} else {
    echo "Parsed OK\n";
    Libxml2::xmlFreeDoc($doc);
}
Libxml2::xmlCleanupParser();
```
