# libcjson build & version

Report the linked cJSON version, then build a JSON document in memory and serialize it (the construction API, distinct from parsing).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcjson\Libcjson;

// Report the linked cJSON library version.
$version = Libcjson::cJSON_Version();
echo 'cJSON version: ' . (string) $version . "\n";

// Build a JSON document programmatically, then serialize it (distinct from parsing).
$root = Libcjson::cJSON_CreateObject();
Libcjson::cJSON_AddStringToObject($root, 'lib', 'cJSON');
Libcjson::cJSON_AddNumberToObject($root, 'answer', 42);
$compact = Libcjson::cJSON_PrintUnformatted($root);
echo 'built: ' . (string) $compact . "\n";
Libcjson::cJSON_Delete($root);
```
