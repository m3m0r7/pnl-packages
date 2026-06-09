# ZeroMQ Package

Package: `libzmq/libzmq`

Base library: ZeroMQ

License: MPL-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libzmq
```

The package requires ZeroMQ headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libzmq` finishes — it comes from the package's `examples` field in `pnlx.json`.
