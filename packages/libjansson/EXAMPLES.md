# libjansson/libjansson examples

```php
use Pnlx\Libjansson\Libjansson;

// Parse a JSON string and read a value from it.
$root = Libjansson::json_loads('{"name":"pnl","version":1}', 0, null);
$nameVal = Libjansson::json_object_get($root, 'name');
$name = Libjansson::json_string_value($nameVal); // returns string "pnl"
echo $name . PHP_EOL;
Libjansson::json_decref($root);
```
