# libcjson/libcjson examples

```php
use Pnlx\Libcjson\Libcjson;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libcjson = $runtime->load(Libcjson::class);

// Parse a JSON string and read a field value
$json = '{"name":"Alice","age":30}';
$root = $libcjson->cJSON_Parse($json);
if (is_null($root)) {
    throw new \RuntimeException('cJSON_Parse failed: ' . $libcjson->cJSON_GetErrorPtr());
}
$nameItem = $libcjson->cJSON_GetObjectItemCaseSensitive($root, 'name');
$name     = $libcjson->cJSON_GetStringValue($nameItem);
echo "name: {$name}\n"; // Alice

$printed = $libcjson->cJSON_Print($root);
echo $printed . "\n";
$libcjson->cJSON_Delete($root);
```
