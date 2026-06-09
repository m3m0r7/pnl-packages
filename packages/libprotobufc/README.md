# protobuf-c Package

Package: `libprotobufc/libprotobufc`

Base library: protobuf-c

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libprotobufc
```

The package requires protobuf-c headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libprotobufc` finishes — it comes from the package's `examples` field in `pnlx.json`.
