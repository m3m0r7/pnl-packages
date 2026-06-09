# libffi Package

Package: `libffi/libffi`

Base library: libffi

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libffi
```

The package requires libffi headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libffi\Libffi;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libffi = $runtime->load(Libffi::class);

// libffi does not expose a runtime version function; the main entry point is
// ffi_prep_cif() to build a call interface, then ffi_call() to invoke it.
// Here we allocate a ffi_cif struct and call ffi_prep_cif for a void(void) CIF.
// FFI_OK = 0, FFI_DEFAULT_ABI = 2 on most platforms, nargs = 0.
$allocator = $runtime->allocator();
$cif = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);

// ffi_prep_cif(cif, abi, nargs, rtype, atypes)
// Full dispatch: create type descriptors with ffi_type_*, then ffi_call(cif, fn, rvalue, avalue).
echo "libffi loaded — use ffi_prep_cif() + ffi_call() to call arbitrary C functions." . PHP_EOL;
```

This snippet is printed when `pnl install libffi` finishes — it comes from the package's `examples` field in `pnlx.json`.
