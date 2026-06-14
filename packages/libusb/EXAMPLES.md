# libusb/libusb examples

```php
use Pnlx\Libusb\Libusb;

if (Libusb::libusb_init(null) !== 0) {
    throw new RuntimeException('libusb_init failed');
}
try {
    // ... enumerate and talk to USB devices ...
} finally {
    Libusb::libusb_exit(null);
}
```
