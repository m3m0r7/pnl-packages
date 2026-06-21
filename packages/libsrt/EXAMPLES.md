# libsrt/libsrt examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsrt\Libsrt;

// srt_getversion() returns the version packed as 0xMMmmpp.
$v = Libsrt::srt_getversion()->toInt();
printf("srt %d.%d.%d\n", ($v >> 16) & 0xff, ($v >> 8) & 0xff, $v & 0xff);
```
