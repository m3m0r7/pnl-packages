        # libudev Package

        Package: `libudev/libudev`

        Base library: libudev

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libudev
        ```

        The package requires libudev headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

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

        This snippet is printed when `pnl install libudev` finishes — it comes from the package's `examples` field in `pnlx.json`.
