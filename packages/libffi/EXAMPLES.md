# libffi/libffi examples

```php
use Pnlx\Libffi\Libffi;

// libffi has no runtime version function; its API is the low-level call-interface
// builder (ffi_prep_cif) plus the dispatcher (ffi_call). What the generator CAN
// surface directly are the ABI/status enums the library defines in <ffi.h>; a
// linked, correctly-generated binding exposes them as namespaced constants.
//
// FFI_OK (= 0) is the success status returned by ffi_prep_cif(); FFI_DEFAULT_ABI
// is the platform's native calling convention. Reading them back confirms the
// header was parsed and the binding is live.
$ok  = (int) (string) \Pnlx\Libffi\FFI_OK;
$abi = (int) (string) \Pnlx\Libffi\FFI_DEFAULT_ABI;
echo "FFI_OK status code: {$ok}\n";
echo "FFI_DEFAULT_ABI: {$abi}\n";

// The real workflow to call an arbitrary C function is:
//   1. Libffi::ffi_prep_cif($cif, FFI_DEFAULT_ABI, $nargs, $rtype, $atypes) // build the call interface
//   2. Libffi::ffi_call($cif, $fn, $rvalue, $avalue)                        // invoke it
// Both map directly to the exported libffi symbols ffi_prep_cif / ffi_call,
// returning FFI_OK on success.
echo "libffi bound — use Libffi::ffi_prep_cif() + Libffi::ffi_call() to call C functions.\n";
```
