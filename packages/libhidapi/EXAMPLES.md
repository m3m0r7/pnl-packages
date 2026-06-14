# libhidapi/libhidapi examples

```php
use Pnlx\Libhidapi\Libhidapi;
use function Pnlx\Util\is_null;

// Initialize HIDAPI and enumerate connected USB HID devices
$rc = Libhidapi::hid_init();
if ($rc === 0) {
    // Enumerate all HID devices (vendor 0, product 0 = all)
    $devs = Libhidapi::hid_enumerate(0, 0);
    $cur = $devs;
    while (!is_null($cur)) {
        echo "Device: " . $cur->manufacturer_string . "\n";
        $cur = $cur->next;
    }
    Libhidapi::hid_free_enumeration($devs);
    Libhidapi::hid_exit();
}
```
