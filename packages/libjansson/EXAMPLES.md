# libjansson/libjansson examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libjansson\Libjansson;

// Parse a JSON string and read a value from it.
$root = Libjansson::json_loads('{"name":"pnl","version":1}', 0, null);
$nameVal = Libjansson::json_object_get($root, 'name');
$name = Libjansson::json_string_value($nameVal); // returns string "pnl"
echo $name . PHP_EOL;
// json_decref is a C `static inline` refcount helper with no exported symbol,
// so it cannot be bound through FFI. Free the freshly-parsed root directly with
// the exported json_delete instead.
Libjansson::json_delete($root);
```
