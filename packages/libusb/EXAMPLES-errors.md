# libusb/libusb error names and capabilities

`libusb_error_name()` and `libusb_strerror()` translate libusb error codes into symbolic names and human-readable messages, while `libusb_has_capability()` probes a runtime feature flag — all without opening a context or a device.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libusb\Libusb;

// libusb_error_name() maps a libusb error code to its symbolic name.
$name = Libusb::libusb_error_name(-5); // LIBUSB_ERROR_NOT_FOUND
echo "error_name(-5): " . (string)$name . PHP_EOL;

// libusb_strerror() turns an error code into a human-readable message.
$msg = Libusb::libusb_strerror(-1); // LIBUSB_ERROR_IO
echo "strerror(-1): " . (string)$msg . PHP_EOL;

// libusb_has_capability() reports a runtime feature flag without opening a device.
$cap = Libusb::libusb_has_capability(0x0000); // LIBUSB_CAP_HAS_CAPABILITY
$capVal = is_object($cap) ? $cap->toInt() : $cap;
echo "has LIBUSB_CAP_HAS_CAPABILITY: " . ($capVal ? 'yes' : 'no') . PHP_EOL;
```
