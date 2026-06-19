# libzmq/libzmq examples

```php
use Pnlx\Libzmq\Libzmq;

// zmq_version() fills three int out-parameters. Pass plain variables by
// reference; the binding allocates the C holders and writes the results back.
$major = 0;
$minor = 0;
$patch = 0;
Libzmq::zmq_version($major, $minor, $patch);
echo "ZeroMQ {$major}.{$minor}.{$patch}\n";

// Explore further: zmq_ctx_new(), zmq_socket(), zmq_bind(),
// zmq_connect(), zmq_send(), zmq_recv(), zmq_close(), zmq_ctx_term(), ...
```
