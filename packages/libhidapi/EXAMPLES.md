# libhidapi/libhidapi examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhidapi\Libhidapi;
use function Pnlx\Util\is_null;

// Initialize HIDAPI and enumerate connected USB HID devices
$rc = Libhidapi::hid_init();
if ($rc->toInt() === 0) {
    // Enumerate all HID devices (vendor 0, product 0 = all)
    $devs = Libhidapi::hid_enumerate(0, 0);
    // hid_enumerate() returns a wrapped struct hid_device_info* linked list;
    // unwrap to the native CData once and walk the `next` pointer.
    $cur = $devs->cdata();
    while (!is_null($cur)) {
        echo "Device: " . $cur->manufacturer_string . "\n";
        $cur = $cur->next;
    }
    Libhidapi::hid_free_enumeration($devs);
    Libhidapi::hid_exit();
}
```
