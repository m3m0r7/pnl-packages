# libunistring/libunistring examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libunistring\Libunistring;

// uc_decimal_value() returns the decimal digit value of a Unicode code point,
// or -1 when it is not a decimal digit.
echo Libunistring::uc_decimal_value(0x0039)->toInt() . PHP_EOL; // 9  (U+0039 is '9')
```
