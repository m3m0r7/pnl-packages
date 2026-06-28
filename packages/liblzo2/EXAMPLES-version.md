# liblzo2/liblzo2 version & config self-check

Read the numeric LZO version and build date, then run the library's internal configuration self-check (returns 0 / LZO_E_OK when the ABI is sane).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblzo2\Liblzo2;

$ver = Liblzo2::lzo_version();
echo 'version number: ' . (is_object($ver) ? $ver->toInt() : $ver) . PHP_EOL; // e.g. 8352

$date = Liblzo2::lzo_version_date();
echo 'version date: ' . (string)$date . PHP_EOL; // e.g. "Mar 01 2017"

$cfg = Liblzo2::_lzo_config_check();
echo 'config check (0 = LZO_E_OK): ' . (is_object($cfg) ? $cfg->toInt() : $cfg) . PHP_EOL; // 0
```
