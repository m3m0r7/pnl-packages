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

## Calling `static inline` helpers

libusb's header defines convenience helpers such as `libusb_cpu_to_le16()` and the
`libusb_fill_*_transfer()` setters as C `static inline` functions. These export no
symbol, so by default the generated method throws `UnsupportedNativeFunctionException`.
To make them callable, opt into compiling a small trampoline shim (this needs a C
compiler at install time) by adding to your project's `pnl.json`:

```jsonc
"compile_options": { "static_inline": true }
```

After reinstalling, `Libusb::libusb_cpu_to_le16(0x1234)` returns the converted value
instead of throwing. See the pnl docs (Configuration → "static inline functions").
