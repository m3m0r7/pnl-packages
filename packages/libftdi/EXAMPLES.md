# libftdi/libftdi examples

```php
use Pnlx\Libftdi\Libftdi;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libftdi = $runtime->load(Libftdi::class);

// Allocate and initialise a new ftdi_context.
$ctx = $libftdi->ftdi_new();
if (is_null($ctx)) {
    throw new \RuntimeException('ftdi_new() failed');
}

// Query the libftdi version information struct.
$vi = $libftdi->ftdi_get_library_version();
echo "libftdi version: {$vi->major}.{$vi->minor}.{$vi->micro}" . PHP_EOL;
echo "Version string: " . $vi->version_str . PHP_EOL;

// ftdi_usb_open(ctx, vendor, product) opens a connected FTDI device.
$libftdi->ftdi_free($ctx);
```
