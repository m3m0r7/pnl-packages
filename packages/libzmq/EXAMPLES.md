# libzmq/libzmq examples

```php
use Pnlx\Libzmq\Libzmq;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libzmq = $runtime->load(Libzmq::class);

// zmq_version() fills three int out-parameters with major/minor/patch.
$major = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$minor = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$patch = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$libzmq->zmq_version($major, $minor, $patch);
echo "ZeroMQ {$major[0]}.{$minor[0]}.{$patch[0]}\n";

// Explore further: zmq_ctx_new(), zmq_socket(), zmq_bind(),
// zmq_connect(), zmq_send(), zmq_recv(), zmq_close(), zmq_ctx_term(), ...
```
