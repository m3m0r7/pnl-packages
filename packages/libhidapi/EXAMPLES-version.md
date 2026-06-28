# libhidapi version string

Read the HIDAPI library version with `hid_version_str()`, a no-argument call that returns the compiled-in version as a string and needs no device or `hid_init()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhidapi\Libhidapi;

$v = Libhidapi::hid_version_str();
echo "HIDAPI version: " . (string)$v . "\n";
```
