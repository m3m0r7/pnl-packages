# libxml2/libxml2 examples

```php
use Pnlx\Libxml2\Libxml2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libxml2 = $runtime->load(Libxml2::class);

// xmlReadMemory() parses an XML document held in a string buffer.
$xml = "<root><item>hello</item></root>";
$doc = $libxml2->xmlReadMemory($xml, strlen($xml), "doc.xml", null, 0);
if (is_null($doc)) {
    echo "Parse failed\n";
} else {
    echo "Parsed OK\n";
    $libxml2->xmlFreeDoc($doc);
}
$libxml2->xmlCleanupParser();
```
