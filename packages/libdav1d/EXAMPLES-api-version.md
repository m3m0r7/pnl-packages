# dav1d API version

`dav1d_version_api()` returns the numeric ABI/API version, which you can unpack into major, minor, and patch components.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libdav1d\Libdav1d;

// dav1d_version_api() returns the numeric API version (major<<16 | minor<<8 | patch).
$api = Libdav1d::dav1d_version_api();
$api = is_object($api) ? $api->toInt() : $api;
echo 'dav1d API version: ' . $api . "\n";
printf("  major=%d minor=%d patch=%d\n", ($api >> 16) & 0xff, ($api >> 8) & 0xff, $api & 0xff);
```
