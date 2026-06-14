# libjansson/libjansson examples

```php
use Pnlx\Libjansson\Libjansson;

$libjansson = new Libjansson();

// Parse a JSON string and read a value from it.
$root = $libjansson->json_loads('{"name":"pnl","version":1}', 0, null);
$nameVal = $libjansson->json_object_get($root, 'name');
$name = $libjansson->json_string_value($nameVal); // returns string "pnl"
echo $name . PHP_EOL;
$libjansson->json_decref($root);
```
