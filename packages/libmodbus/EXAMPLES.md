# libmodbus/libmodbus examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmodbus\Libmodbus;
use function Pnlx\Util\is_null;

// Create a Modbus TCP context, connect, read holding registers, then close.
$ctx = Libmodbus::modbus_new_tcp('192.168.1.10', 502);
if (is_null($ctx)) {
    throw new \RuntimeException('modbus_new_tcp failed');
}
Libmodbus::modbus_set_slave($ctx, 1);
if (Libmodbus::modbus_connect($ctx)->toInt() !== -1) {
    // modbus_read_registers: start=0, count=2; explore returned register array
    Libmodbus::modbus_read_registers($ctx, 0, 2, null);
    Libmodbus::modbus_close($ctx);
}
Libmodbus::modbus_free($ctx);
```
