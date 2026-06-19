# libcares/libcares examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcares\Libcares;

// Initialise the c-ares library and print its version string
$rc = Libcares::ares_library_init(1)->toInt(); // ARES_LIB_INIT_ALL = 1
if ($rc !== 0) {
    throw new \RuntimeException("ares_library_init failed: {$rc}");
}

// ares_version() writes the version number into its int out-parameter and
// returns the version string. Pass a plain variable by reference.
$versionNumber = 0;
$versionStr    = Libcares::ares_version($versionNumber);
echo "c-ares version: {$versionStr} ({$versionNumber})\n";

// Asynchronous DNS: Libcares::ares_init($channel) then Libcares::ares_gethostbyname(...)
Libcares::ares_library_cleanup();
```
