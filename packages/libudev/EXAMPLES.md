# libudev/libudev examples

```php
use Pnlx\Libudev\Libudev;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libudev = $runtime->load(Libudev::class);

// Create a udev context, then release it.
$udev = $libudev->udev_new();
$libudev->udev_unref($udev);

// Explore further: udev_enumerate_new(), udev_enumerate_scan_devices(),
// udev_device_new_from_syspath(), udev_monitor_new_from_netlink(), ...
```
