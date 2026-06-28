# libz3 error messages

`Z3_get_error_msg()` translates a Z3 error code into a human-readable message.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libz3\Libz3;

// Translate Z3 error codes to human-readable messages via Z3_get_error_msg().
$cfg = Libz3::Z3_mk_config();
$ctx = Libz3::Z3_mk_context($cfg);

foreach ([0, 3, 10] as $code) {
    $msg = Libz3::Z3_get_error_msg($ctx, $code);
    echo "error $code: " . (string)$msg . "\n";
}

Libz3::Z3_del_context($ctx);
Libz3::Z3_del_config($cfg);
```
