# libmsgpack/libmsgpack examples

```php
use Pnlx\Libmsgpack\Libmsgpack;

// Pack an integer into a msgpack buffer
$sbuf = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$packer = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);

Libmsgpack::msgpack_sbuffer_init($sbuf);
Libmsgpack::msgpack_packer_init($packer, $sbuf, null);
Libmsgpack::msgpack_pack_int($packer, 42);

echo "Packed bytes: " . $sbuf->size . "\n";
// ... transmit $sbuf->data ...

Libmsgpack::msgpack_sbuffer_destroy($sbuf);
```
