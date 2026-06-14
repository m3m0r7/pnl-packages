# libexpat/libexpat examples

```php
use Pnlx\Libexpat\Libexpat;
use function Pnlx\Util\is_null;

// Query Expat's version string (e.g. "expat_2.6.2").
$version = Libexpat::XML_ExpatVersion();
echo "Expat version: " . $version . PHP_EOL;

// Create a parser, feed a small XML document, then free it.
$parser = Libexpat::XML_ParserCreate(null);
if (is_null($parser)) {
    throw new \RuntimeException('XML_ParserCreate failed');
}
$xml = '<root><child attr="hello">world</child></root>';
Libexpat::XML_Parse($parser, $xml, strlen($xml), 1);
Libexpat::XML_ParserFree($parser);
echo "Parsed successfully." . PHP_EOL;
```
