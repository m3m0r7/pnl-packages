# libffi/libffi examples

```php
use Pnlx\Libffi\Libffi;

// libffi does not expose a runtime version function; the main entry point is
// ffi_prep_cif() to build a call interface, then ffi_call() to invoke it.
// Here we allocate a ffi_cif struct and call ffi_prep_cif for a void(void) CIF.
// FFI_OK = 0, FFI_DEFAULT_ABI = 2 on most platforms, nargs = 0.
$allocator = (new \Pnlx\FFI\Allocator());
$cif = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);

// ffi_prep_cif(cif, abi, nargs, rtype, atypes)
// Full dispatch: create type descriptors with ffi_type_*, then ffi_call(cif, fn, rvalue, avalue).
echo "libffi loaded — use ffi_prep_cif() + ffi_call() to call arbitrary C functions." . PHP_EOL;
```
