# libusb/libusb examples

```php
use Pnlx\Libusb\Libusb;

// libusb_init() initialises a session context (a libusb_context** handle written
// back by reference); pair it with libusb_exit(). No device is required.
$ctx = null;
$rc = Libusb::libusb_init($ctx);
if ($rc === 0) {
    echo "libusb session initialised\n";
    Libusb::libusb_exit($ctx);
} else {
    echo "libusb_init() returned {$rc}\n"; // e.g. no usbfs in a container; the call still dispatched
}
```
