# libxml2/libxml2 examples

```php
use Pnlx\Libxml2\Libxml2;
use function Pnlx\Util\is_null;

$libxml2 = new Libxml2();

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
