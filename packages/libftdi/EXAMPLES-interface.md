# libftdi interface selection

Pick which interface (A/B/C/D) of a multi-channel FTDI chip a context will use; it only updates the context and returns 0 on success, so no device is required.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libftdi\Libftdi;
use function Pnlx\Util\is_null;

$num = fn($x) => is_object($x) ? $x->toInt() : $x;

// ftdi_set_interface() configures the channel a freshly created context targets.
$ctx = Libftdi::ftdi_new();
if (!is_null($ctx)) {
    $rc = Libftdi::ftdi_set_interface($ctx, 1); // INTERFACE_A
    echo 'ftdi_set_interface -> ' . ($num($rc) === 0 ? "ok\n" : 'rc=' . $num($rc) . "\n");
    Libftdi::ftdi_free($ctx);
}
```
