# msgpack-c Package

Package: `libmsgpack/libmsgpack`

Base library: msgpack-c

License: BSL-1.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmsgpack
```

The package requires msgpack-c headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libmsgpack` finishes — it comes from the package's `examples` field in `pnlx.json`.
