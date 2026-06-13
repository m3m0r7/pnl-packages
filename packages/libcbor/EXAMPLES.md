# libcbor/libcbor examples

```php
use Pnlx\Libcbor\Libcbor;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libcbor = $runtime->load(Libcbor::class);

// Build a CBOR unsigned integer item.
$item = $libcbor->cbor_build_uint32(1234);
// ... serialise or inspect $item, then release it with cbor_decref().

// Explore further: cbor_load(), cbor_serialize_alloc(),
// cbor_new_definite_map(), cbor_map_add(), cbor_decref(), ...
```
