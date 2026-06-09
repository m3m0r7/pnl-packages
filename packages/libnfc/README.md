# libnfc Package

Package: `libnfc/libnfc`

Base library: libnfc

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnfc
```

The package requires libnfc headers such as `nfc/nfc.h`. It sets `symbol_prefix` to `nfc` because the library key is `libnfc` while exported functions use the `nfc_*` prefix.

## PHP usage

```php
use Pnlx\Libnfc\Libnfc;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libnfc = $runtime->load(Libnfc::class);

// Query the library version (returns char* → PHP string)
$version = $libnfc->nfc_version();
echo "libnfc version: $version\n";

// Initialise a context, open the first available NFC device
$ctx = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libnfc->nfc_init($ctx);
$device = $libnfc->nfc_open($ctx, null);
if (is_null($device)) {
    echo "No NFC device found\n";
} else {
    // ... use $device ...
    $libnfc->nfc_close($device);
}
$libnfc->nfc_exit($ctx);
```

This snippet is printed when `pnl install libnfc` finishes — it comes from the package's `examples` field in `pnlx.json`.
