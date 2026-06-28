# libzmq error and capability diagnostics

Translate an error number to text, read the calling thread's last error, and probe an optional build capability, all without a context or socket.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libzmq\Libzmq;

// zmq_strerror() maps a ZeroMQ/system error number to a human-readable message.
$msg = Libzmq::zmq_strerror(11);
echo 'message for errno 11: ' . (string)$msg . PHP_EOL;

// zmq_errno() returns the calling thread's last ZeroMQ error number.
$errno = Libzmq::zmq_errno();
echo 'last errno: ' . (is_object($errno) ? $errno->toInt() : $errno) . PHP_EOL;

// zmq_has() reports whether the library was built with a capability.
$ipc = Libzmq::zmq_has('ipc');
echo 'has ipc: ' . (is_object($ipc) ? $ipc->toInt() : $ipc) . PHP_EOL;
```
