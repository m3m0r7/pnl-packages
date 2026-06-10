# libnfc/libnfc examples

```php
use Pnlx\Libnfc\Libnfc;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libnfc = $runtime->load(Libnfc::class);

// Query the library version (returns char* → PHP string)
$version = $libnfc->nfc_version();
echo "libnfc version: $version\n";

// Initialise a context, open the first available NFC device
$ctx = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libnfc->nfc_init($ctx);
$device = $libnfc->nfc_open($ctx, null);
if (is_null($device)) {
    echo "No NFC device found\n";
} else {
    // ... use $device ...
    $libnfc->nfc_close($device);
}
$libnfc->nfc_exit($ctx);
```
