# libhiredis sds dynamic strings

hiredis bundles `sds`, a small dynamic-string library you can use without any Redis connection: build an empty string, wrap a PHP string, or format an integer.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhiredis\Libhiredis;

// sds is hiredis's dynamic string library, usable without any Redis connection.
$empty = Libhiredis::sdsempty();
echo "empty len: " . strlen((string)$empty) . "\n";

$greeting = Libhiredis::sdsnew('hello from sds');
echo "string: " . (string)$greeting . "\n";

$num = Libhiredis::sdsfromlonglong(9876543210);
echo "from long long: " . (string)$num . "\n";
```
