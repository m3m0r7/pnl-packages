# libnfc/libnfc examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnfc\Libnfc;
use function Pnlx\Util\is_null;

// Query the library version (returns char* → PHP string)
$version = Libnfc::nfc_version();
echo "libnfc version: $version\n";

// Initialise a context, open the first available NFC device. nfc_init takes an
// `nfc_context **` out-parameter, so pass a variable by reference: the call writes
// the context handle back into $ctx (no manual allocation needed).
$ctx = null;
Libnfc::nfc_init($ctx);
$device = Libnfc::nfc_open($ctx, null);
if (is_null($device)) {
    echo "No NFC device found\n";
} else {
    // ... use $device ...
    Libnfc::nfc_close($device);
}
Libnfc::nfc_exit($ctx);
```
