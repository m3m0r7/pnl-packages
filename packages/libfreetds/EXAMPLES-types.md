# libfreetds server type helpers

Inspect FreeTDS server data types: resolve a type token to its printable name and test type conversions, no connection required.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfreetds\Libfreetds;

// dbprtype() turns a server type token into its printable name.
foreach ([47 => 'SYBCHAR', 56 => 'SYBINT4', 62 => 'SYBFLT8'] as $token => $name) {
    $type = Libfreetds::dbprtype($token);
    echo "$name ($token) -> " . (string)$type . PHP_EOL;
}

// dbwillconvert() reports whether one server type can be converted to another.
$ok = Libfreetds::dbwillconvert(56, 47); // SYBINT4 -> SYBCHAR
$ok = is_object($ok) ? $ok->toInt() : $ok;
echo "int convertible to char: " . ($ok ? "yes" : "no") . PHP_EOL;
```
