# libmodbus Package

Package: `libmodbus/libmodbus`

Base library: libmodbus

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmodbus
```

The package requires libmodbus headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmodbus\Libmodbus;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libmodbus = $runtime->load(Libmodbus::class);

// Create a Modbus TCP context, connect, read holding registers, then close.
$ctx = $libmodbus->modbus_new_tcp('192.168.1.10', 502);
if (is_null($ctx)) {
    throw new \RuntimeException('modbus_new_tcp failed');
}
$libmodbus->modbus_set_slave($ctx, 1);
if ($libmodbus->modbus_connect($ctx) !== -1) {
    // modbus_read_registers: start=0, count=2; explore returned register array
    $libmodbus->modbus_read_registers($ctx, 0, 2, null);
    $libmodbus->modbus_close($ctx);
}
$libmodbus->modbus_free($ctx);
```

This snippet is printed when `pnl install libmodbus` finishes — it comes from the package's `examples` field in `pnlx.json`.
