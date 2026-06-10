# libusb/libusb examples

```php
use Pnlx\Libusb\Libusb;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$usb = $runtime->load(Libusb::class);

if ($usb->libusb_init(null) !== 0) {
    throw new RuntimeException('libusb_init failed');
}
try {
    // ... enumerate and talk to USB devices ...
} finally {
    $usb->libusb_exit(null);
}
```
