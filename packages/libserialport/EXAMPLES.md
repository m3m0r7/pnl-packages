# libserialport/libserialport examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libserialport\Libserialport;
use function Pnlx\Util\is_null;

// Get a port handle by name. sp_get_port_by_name takes a `struct sp_port **`
// out-parameter, so pass a variable by reference: the call writes the port handle
// back into $port (no manual allocation, and $port is the handle to use directly).
// The call returns an `Enums\sp_return` case — read its C value with toInt(), or
// its label with ->name (PHP enums cannot be string-cast directly).
$port = null;
$rc = Libserialport::sp_get_port_by_name('/dev/ttyUSB0', $port);
if ($rc->toInt() !== 0) { // not SP_OK (0)
    echo "No serial port at /dev/ttyUSB0 (sp_get_port_by_name: {$rc->name})\n";
    return;
}

Libserialport::sp_open($port, 3); // SP_MODE_READ_WRITE = 3
Libserialport::sp_set_baudrate($port, 9600);

// Write and read data
Libserialport::sp_blocking_write($port, 'AT\r\n', 4, 1000);
$buf = Libserialport::sp_blocking_read($port, 64, 1000);
echo "Response: {$buf}\n";

Libserialport::sp_close($port);
Libserialport::sp_free_port($port);
```
