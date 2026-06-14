# libprotobufc/libprotobufc examples

```php
use Pnlx\Libprotobufc\Libprotobufc;

// Query protobuf-c library version
$versionStr = Libprotobufc::protobuf_c_version();
$versionNum = Libprotobufc::protobuf_c_version_number();
echo "protobuf-c version: {$versionStr} ({$versionNum})\n";

// Packing/unpacking messages requires a generated C descriptor; see protobuf-c docs:
// Libprotobufc::protobuf_c_message_pack($message, $out)     // serialise
// Libprotobufc::protobuf_c_message_unpack($desc, null, $len, $data) // deserialise
```
