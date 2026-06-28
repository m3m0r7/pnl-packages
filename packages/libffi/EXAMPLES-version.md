# libffi/libffi — runtime version and default ABI

Query libffi's own build identity at runtime with `ffi_get_version()` / `ffi_get_version_number()` and read the platform's native calling-convention code via `ffi_get_default_abi()` (libffi >= 3.5).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libffi\Libffi;

// libffi exposes its own build identity at runtime (libffi >= 3.5):
// ffi_get_version() returns the dotted version string, ffi_get_version_number()
// the same encoded as a single integer, and ffi_get_default_abi() the numeric
// code of the platform's native calling convention.
$ver = Libffi::ffi_get_version();
$num = Libffi::ffi_get_version_number();
$abi = Libffi::ffi_get_default_abi();

echo 'libffi version: ' . (string) $ver . "\n";
echo 'version number: ' . (is_object($num) ? $num->toInt() : $num) . "\n";
echo 'default ABI code: ' . (is_object($abi) ? $abi->toInt() : $abi) . "\n";
```
