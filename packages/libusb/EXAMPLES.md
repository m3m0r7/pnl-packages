# libusb/libusb examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libusb\Libusb;

// libusb_init() initialises a session context (a libusb_context** handle written
// back by reference); pair it with libusb_exit(). No device is required.
// The int result comes back as a \Pnlx\Types\Int_ wrapper, so compare via ->toInt().
$ctx = null;
$rc = Libusb::libusb_init($ctx);
if ($rc->toInt() === 0) {
    echo "libusb session initialised\n";
    Libusb::libusb_exit($ctx);
} else {
    echo "libusb_init() returned {$rc}\n"; // e.g. no usbfs in a container; the call still dispatched
}
```
