# libcbor/libcbor — inspecting an item

Build a CBOR item, then read it back with the inspection helpers `cbor_isa_uint()`, `cbor_get_uint8()`, and `cbor_typeof()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcbor\Libcbor;

// Build a CBOR unsigned-int item, then INSPECT it rather than serialise it.
$item = Libcbor::cbor_build_uint8(42);

// cbor_isa_uint() / cbor_get_uint8() read the value back out; the typed
// getters return wrapped scalars, so unwrap with toInt().
echo 'is uint : ' . (Libcbor::cbor_isa_uint($item)->toInt() ? 'true' : 'false') . PHP_EOL;
echo 'value   : ' . Libcbor::cbor_get_uint8($item)->toInt() . PHP_EOL;

// cbor_typeof() returns the high-level item type as a PHP enum case.
echo 'type    : ' . Libcbor::cbor_typeof($item)->name . PHP_EOL;
```
