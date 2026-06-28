# libnss version check and init status

Verify the loaded NSS is recent enough with `NSS_VersionCheck()` and query whether the library has been initialised with `NSS_IsInitialized()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnss\Libnss;

// NSS_VersionCheck() reports whether the loaded NSS is at least the requested version.
$ok = Libnss::NSS_VersionCheck('3.0');
$ok = is_object($ok) ? $ok->toInt() : $ok;
echo 'NSS >= 3.0 compatible: ' . ($ok ? 'yes' : 'no') . PHP_EOL;

// NSS_IsInitialized() reports whether NSS_Init has been called yet (0 before init).
$init = Libnss::NSS_IsInitialized();
$init = is_object($init) ? $init->toInt() : $init;
echo 'NSS initialized: ' . ($init ? 'yes' : 'no') . PHP_EOL;
```
