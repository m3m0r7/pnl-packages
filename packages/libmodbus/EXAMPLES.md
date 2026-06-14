# libmodbus/libmodbus examples

```php
use Pnlx\Libmodbus\Libmodbus;
use function Pnlx\Util\is_null;

$libmodbus = new Libmodbus();

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
