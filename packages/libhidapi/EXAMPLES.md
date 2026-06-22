# libhidapi/libhidapi examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhidapi\Libhidapi;

// Initialize HIDAPI and enumerate connected USB HID devices.
$rc = Libhidapi::hid_init();
if ($rc->toInt() === 0) {
    // hid_enumerate(0, 0) lists every HID device. It returns a typed
    // `hid_device_info` wrapper (or null when no device is connected).
    $devs = Libhidapi::hid_enumerate(0, 0);

    if ($devs === null) {
        echo "No HID devices found.\n";
    } else {
        // Walk the linked list through the typed accessors. `manufacturer_string`
        // and friends are C `wchar_t *`, decoded to PHP strings by the generated
        // getters (getManufacturerString()/getProductString()/getSerialNumber()).
        for ($dev = $devs; $dev !== null; $dev = $dev->getNext()) {
            printf(
                "%04x:%04x  %s %s\n",
                $dev->getVendorId(),
                $dev->getProductId(),
                $dev->getManufacturerString() ?? '(unknown)',
                $dev->getProductString() ?? ''
            );
        }
        Libhidapi::hid_free_enumeration($devs);
    }

    Libhidapi::hid_exit();
}
```
