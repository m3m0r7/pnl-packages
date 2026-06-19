# libudev/libudev examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libudev\Libudev;

// Create a udev context, then release it.
$udev = Libudev::udev_new();
Libudev::udev_unref($udev);

// Explore further: udev_enumerate_new(), udev_enumerate_scan_devices(),
// udev_device_new_from_syspath(), udev_monitor_new_from_netlink(), ...
```
