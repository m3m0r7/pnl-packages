# libhwloc/libhwloc examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhwloc\Libhwloc;

// hwloc_get_api_version() returns the ABI version as a packed 0xMMmmpp integer.
$v = Libhwloc::hwloc_get_api_version()->toInt();
printf("hwloc API 0x%06x\n", $v);
```
