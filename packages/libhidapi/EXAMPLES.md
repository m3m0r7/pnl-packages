# libhidapi/libhidapi examples

```php
use Pnlx\Libhidapi\Libhidapi;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libhidapi = $runtime->load(Libhidapi::class);

// Initialize HIDAPI and enumerate connected USB HID devices
$rc = $libhidapi->hid_init();
if ($rc === 0) {
    // Enumerate all HID devices (vendor 0, product 0 = all)
    $devs = $libhidapi->hid_enumerate(0, 0);
    $cur = $devs;
    while (!is_null($cur)) {
        echo "Device: " . $cur->manufacturer_string . "\n";
        $cur = $cur->next;
    }
    $libhidapi->hid_free_enumeration($devs);
    $libhidapi->hid_exit();
}
```
