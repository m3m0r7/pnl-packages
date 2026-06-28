# libxml2 UTF-8 string helpers

libxml2 exposes UTF-8 aware string utilities — `xmlStrlen()`, `xmlUTF8Strlen()`, and `xmlCheckUTF8()` — that work on plain strings without parsing a document.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libxml2\Libxml2;

// libxml2 ships UTF-8 aware string helpers usable without parsing a document.
$text = "héllo wörld";

$bytes = Libxml2::xmlStrlen($text);
echo "byte length: " . (is_object($bytes) ? $bytes->toInt() : $bytes) . "\n";

$chars = Libxml2::xmlUTF8Strlen($text);
echo "utf-8 characters: " . (is_object($chars) ? $chars->toInt() : $chars) . "\n";

$valid = Libxml2::xmlCheckUTF8($text);
echo "well-formed utf-8: " . ((is_object($valid) ? $valid->toInt() : $valid) ? "yes" : "no") . "\n";
```
