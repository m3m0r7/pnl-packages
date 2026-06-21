# libimagequant/libimagequant examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libimagequant\Libimagequant;

// liq_version() returns the libimagequant version encoded as MMmmpp (e.g. 40001).
echo Libimagequant::liq_version()->toInt() . PHP_EOL;
```
