# libraw/libraw version & camera info

`libraw_version()`, `libraw_versionNumber()` and `libraw_cameraCount()` report build and capability info without allocating a processing handle.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libraw\Libraw;

// libraw_version() returns the library version string.
echo (string) Libraw::libraw_version() . PHP_EOL; // e.g. 0.21.5-Release

// libraw_versionNumber() returns the packed numeric version.
$num = Libraw::libraw_versionNumber();
echo (is_object($num) ? $num->toInt() : $num) . PHP_EOL; // e.g. 5381

// libraw_cameraCount() reports how many cameras LibRaw recognises.
$cams = Libraw::libraw_cameraCount();
echo (is_object($cams) ? $cams->toInt() : $cams) . PHP_EOL; // e.g. 1181
```
