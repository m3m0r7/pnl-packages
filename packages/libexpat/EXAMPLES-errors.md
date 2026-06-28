# libexpat/libexpat error-handling examples

Map Expat error codes to messages with `XML_ErrorString`, and recover the error code from a failed parse via `XML_GetErrorCode`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libexpat\Libexpat;

// Map well-known Expat error codes to their human-readable messages.
foreach ([1, 2, 4] as $code) {
    echo "error {$code}: " . (string)Libexpat::XML_ErrorString($code) . PHP_EOL;
}

// Parse a malformed document, then report the resulting error.
$parser = Libexpat::XML_ParserCreate(null);
$bad = '<root><unclosed></root>';
Libexpat::XML_Parse($parser, $bad, strlen($bad), 1);
$code = Libexpat::XML_GetErrorCode($parser);
$code = is_object($code) ? $code->toInt() : (int)$code;
echo "malformed XML -> error {$code}: " . (string)Libexpat::XML_ErrorString($code) . PHP_EOL;
Libexpat::XML_ParserFree($parser);
```
