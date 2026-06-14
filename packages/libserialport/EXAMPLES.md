# libserialport/libserialport examples

```php
use Pnlx\Libserialport\Libserialport;
use function Pnlx\Util\is_null;

// Get a port handle by name and open it
$port = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = Libserialport::sp_get_port_by_name('/dev/ttyUSB0', $port);
if ($rc !== 0) { // SP_OK = 0
    throw new \RuntimeException('sp_get_port_by_name failed: ' . $rc);
}

Libserialport::sp_open($port[0], 3); // SP_MODE_READ_WRITE = 3
Libserialport::sp_set_baudrate($port[0], 9600);

// Write and read data
Libserialport::sp_blocking_write($port[0], 'AT\r\n', 4, 1000);
$buf = Libserialport::sp_blocking_read($port[0], 64, 1000);
echo "Response: {$buf}\n";

Libserialport::sp_close($port[0]);
Libserialport::sp_free_port($port[0]);
```
