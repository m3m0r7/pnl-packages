# libcjson/libcjson examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcjson\Libcjson;
use function Pnlx\Util\is_null;

// Parse a JSON string and read a field value
$json = '{"name":"Alice","age":30}';
$root = Libcjson::cJSON_Parse($json);
if (is_null($root)) {
    throw new \RuntimeException('cJSON_Parse failed: ' . Libcjson::cJSON_GetErrorPtr());
}
$nameItem = Libcjson::cJSON_GetObjectItemCaseSensitive($root, 'name');
$name     = Libcjson::cJSON_GetStringValue($nameItem);
echo "name: {$name}\n"; // Alice

$printed = Libcjson::cJSON_Print($root);
echo $printed . "\n";
Libcjson::cJSON_Delete($root);
```
