# libp11kit/libp11kit examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libp11kit\Libp11kit;

// p11_kit_check_version() returns 1 when the runtime p11-kit is at least the
// requested (major, minor, micro) version, otherwise 0.
echo Libp11kit::p11_kit_check_version(0, 0, 0) . PHP_EOL; // 1
```
