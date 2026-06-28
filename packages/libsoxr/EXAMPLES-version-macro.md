# libsoxr SOXR_VERSION macro

Use the `SOXR_VERSION` header macro to pack major/minor/patch numbers into a single integer (and decode it back).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use function Pnlx\Func\Libsoxr\SOXR_VERSION;

// SOXR_VERSION packs major/minor/patch into a single integer (header macro).
$packed = SOXR_VERSION(0, 1, 3);
echo 'packed = ' . $packed . PHP_EOL;
printf("major=%d minor=%d patch=%d\n", ($packed >> 16) & 0xff, ($packed >> 8) & 0xff, $packed & 0xff);
```
