# libjansson version and integer values

Report the linked Jansson version string, then build an integer JSON value and read its scalar back out.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libjansson\Libjansson;

// Report the linked Jansson version, then round-trip an integer JSON value.
echo 'jansson ' . (string)Libjansson::jansson_version_str() . PHP_EOL;

$node = Libjansson::json_integer(42);
$value = Libjansson::json_integer_value($node);
echo 'integer value: ' . (is_object($value) ? $value->toInt() : $value) . PHP_EOL;
Libjansson::json_delete($node);
```
