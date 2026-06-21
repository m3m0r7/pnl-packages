# libserialport/libserialport examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libserialport\Libserialport;
use function Pnlx\Util\is_null;

// Get a port handle by name. sp_get_port_by_name takes a `struct sp_port **`
// out-parameter, so pass a variable by reference: the call writes the port handle
// back into $port (no manual allocation, and $port is the handle to use directly).
$port = null;
$rc = Libserialport::sp_get_port_by_name('/dev/ttyUSB0', $port);
if ($rc->toInt() !== 0) { // SP_OK = 0
    throw new \RuntimeException('sp_get_port_by_name failed: ' . $rc);
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
