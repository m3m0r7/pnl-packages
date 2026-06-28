# libzimg buffer and API-version helpers

These pure helpers compute a circular-buffer line mask and pack an API major/minor pair into a single integer, with no FFI image allocation.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libzimg\Libzimg;
use function Pnlx\Func\Libzimg\ZIMG_MAKE_API_VERSION;

// zimg_select_buffer_mask() normalizes a line count into a circular-buffer mask.
$mask = Libzimg::zimg_select_buffer_mask(8);
echo 'buffer mask for 8 lines: ' . (is_object($mask) ? $mask->toInt() : $mask) . PHP_EOL;

// ZIMG_MAKE_API_VERSION() packs an API major/minor pair into one integer.
$api = ZIMG_MAKE_API_VERSION(2, 4);
echo 'packed API version (2.4): ' . (is_object($api) ? $api->toInt() : $api) . PHP_EOL;
```
