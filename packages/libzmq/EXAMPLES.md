# libzmq/libzmq examples

```php
use Pnlx\Libzmq\Libzmq;

// zmq_version() fills three int out-parameters with major/minor/patch.
$major = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$minor = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$patch = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
Libzmq::zmq_version($major, $minor, $patch);
echo "ZeroMQ {$major[0]}.{$minor[0]}.{$patch[0]}\n";

// Explore further: zmq_ctx_new(), zmq_socket(), zmq_bind(),
// zmq_connect(), zmq_send(), zmq_recv(), zmq_close(), zmq_ctx_term(), ...
```
