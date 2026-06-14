# libcares/libcares examples

```php
use Pnlx\Libcares\Libcares;

// Initialise the c-ares library and print its version string
$rc = Libcares::ares_library_init(1); // ARES_LIB_INIT_ALL = 1
if ($rc !== 0) {
    throw new \RuntimeException("ares_library_init failed: {$rc}");
}

$versionNumber = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$versionStr    = Libcares::ares_version($versionNumber);
echo "c-ares version: {$versionStr}\n";

// Asynchronous DNS: Libcares::ares_init($channel) then Libcares::ares_gethostbyname(...)
Libcares::ares_library_cleanup();
```
