# libserialport Package

Package: `libserialport/libserialport`

Base library: libserialport

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libserialport
```

The package requires libserialport headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libserialport\Libserialport;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libserialport = $runtime->load(Libserialport::class);

// Get a port handle by name and open it
$port = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = $libserialport->sp_get_port_by_name('/dev/ttyUSB0', $port);
if ($rc !== 0) { // SP_OK = 0
    throw new \RuntimeException('sp_get_port_by_name failed: ' . $rc);
}

$libserialport->sp_open($port[0], 3); // SP_MODE_READ_WRITE = 3
$libserialport->sp_set_baudrate($port[0], 9600);

// Write and read data
$libserialport->sp_blocking_write($port[0], 'AT\r\n', 4, 1000);
$buf = $libserialport->sp_blocking_read($port[0], 64, 1000);
echo "Response: {$buf}\n";

$libserialport->sp_close($port[0]);
$libserialport->sp_free_port($port[0]);
```

This snippet is printed when `pnl install libserialport` finishes — it comes from the package's `examples` field in `pnlx.json`.
