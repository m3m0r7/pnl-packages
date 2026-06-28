# liburiparser/liburiparser runtime version

`uriBaseRuntimeVersionA()` returns the version string of the uriparser shared library actually loaded at runtime, with no parsing or struct allocation required.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liburiparser\Liburiparser;

// uriBaseRuntimeVersionA() reports the uriparser runtime version string.
$v = Liburiparser::uriBaseRuntimeVersionA();
echo "uriparser runtime version: " . (string)$v . PHP_EOL;
```
