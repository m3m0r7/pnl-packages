# libmsgpack/libmsgpack examples

```php
use Pnlx\Libmsgpack\Libmsgpack;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libmsgpack = $runtime->load(Libmsgpack::class);

// Pack an integer into a msgpack buffer
$sbuf = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$packer = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);

$libmsgpack->msgpack_sbuffer_init($sbuf);
$libmsgpack->msgpack_packer_init($packer, $sbuf, null);
$libmsgpack->msgpack_pack_int($packer, 42);

echo "Packed bytes: " . $sbuf->size . "\n";
// ... transmit $sbuf->data ...

$libmsgpack->msgpack_sbuffer_destroy($sbuf);
```
