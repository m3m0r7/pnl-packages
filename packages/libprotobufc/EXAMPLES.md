# libprotobufc/libprotobufc examples

```php
use Pnlx\Libprotobufc\Libprotobufc;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libprotobufc = $runtime->load(Libprotobufc::class);

// Query protobuf-c library version
$versionStr = $libprotobufc->protobuf_c_version();
$versionNum = $libprotobufc->protobuf_c_version_number();
echo "protobuf-c version: {$versionStr} ({$versionNum})\n";

// Packing/unpacking messages requires a generated C descriptor; see protobuf-c docs:
// $libprotobufc->protobuf_c_message_pack($message, $out)     // serialise
// $libprotobufc->protobuf_c_message_unpack($desc, null, $len, $data) // deserialise
```
