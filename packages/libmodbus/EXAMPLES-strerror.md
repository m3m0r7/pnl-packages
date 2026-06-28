# libmodbus error-code lookup with modbus_strerror

Turn numeric libmodbus protocol exception codes and standard system errno values into human-readable messages.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmodbus\Libmodbus;
use const Pnlx\Libmodbus\MODBUS_ENOBASE;

// modbus_strerror() turns a numeric error code into a human-readable string.
// libmodbus protocol exceptions live at MODBUS_ENOBASE + exception number.
$enobase = is_object(MODBUS_ENOBASE) ? MODBUS_ENOBASE->toInt() : MODBUS_ENOBASE;
foreach ([1 => 'illegal function', 2 => 'illegal data address', 3 => 'illegal data value'] as $exc => $label) {
    $msg = Libmodbus::modbus_strerror($enobase + $exc);
    echo $label . ': ' . (string)$msg . PHP_EOL;
}

// It also resolves standard system errno values.
$msg = Libmodbus::modbus_strerror(2); // ENOENT
echo 'errno 2: ' . (string)$msg . PHP_EOL;
```
