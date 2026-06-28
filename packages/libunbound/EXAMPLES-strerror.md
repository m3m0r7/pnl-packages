# libunbound error-code lookup

`ub_strerror()` translates a libunbound result code into a human-readable message.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libunbound\Libunbound;

// ub_strerror() maps a libunbound result code to a human-readable message.
foreach ([0, -1, -2, -3] as $code) {
    $msg = Libunbound::ub_strerror($code);
    echo $code . ' => ' . (string)$msg . PHP_EOL;
}
// 0 => no error
// -1 => socket io error
// -2 => out of memory
// -3 => syntax error
```
