# liblz4/liblz4 version & error-name lookup

Query the LZ4 runtime version (number and string) and resolve a frame error code to its human-readable name without touching any compression state.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblz4\Liblz4;

$num = Liblz4::LZ4_versionNumber();
echo 'version number: ' . (is_object($num) ? $num->toInt() : $num) . PHP_EOL; // e.g. 11000

$str = Liblz4::LZ4_versionString();
echo 'version string: ' . (string)$str . PHP_EOL; // e.g. "1.10.0"

$err = Liblz4::LZ4F_getErrorName(0);
echo 'error name for code 0: ' . (string)$err . PHP_EOL; // "Unspecified error code"
```
