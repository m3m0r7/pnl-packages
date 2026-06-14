# libusb/libusb examples

```php
use Pnlx\Libusb\Libusb;

$usb = new Libusb();

if ($usb->libusb_init(null) !== 0) {
    throw new RuntimeException('libusb_init failed');
}
try {
    // ... enumerate and talk to USB devices ...
} finally {
    $usb->libusb_exit(null);
}
```
