# libusb Package

Package: `libusb/libusb`

Base library: libusb 1.0

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install libusb
```

The package requires libusb and `libusb-1.0/libusb.h` to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This same snippet is printed when `pnl install libusb` finishes — it comes from the package's `examples` field in `pnlx.json`.
