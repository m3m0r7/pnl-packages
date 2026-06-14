# libftdi/libftdi examples

```php
use Pnlx\Libftdi\Libftdi;
use function Pnlx\Util\is_null;

// Allocate and initialise a new ftdi_context.
$ctx = Libftdi::ftdi_new();
if (is_null($ctx)) {
    throw new \RuntimeException('ftdi_new() failed');
}

// Query the libftdi version information struct.
$vi = Libftdi::ftdi_get_library_version();
echo "libftdi version: {$vi->major}.{$vi->minor}.{$vi->micro}" . PHP_EOL;
echo "Version string: " . $vi->version_str . PHP_EOL;

// ftdi_usb_open(ctx, vendor, product) opens a connected FTDI device.
Libftdi::ftdi_free($ctx);
```
