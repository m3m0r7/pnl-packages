# libftdi1 Package

Package: `libftdi/libftdi`

Base library: libftdi1

License: LGPL-2.1-only

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libftdi
```

The package requires libftdi1 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libftdi` finishes — it comes from the package's `examples` field in `pnlx.json`.
