# librav1e/librav1e status & full version

`rav1e_status_to_str()` maps an encoder status code to a human-readable string, while `rav1e_version_full()` returns the full version — both pure calls needing no encoder context.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Librav1e\Librav1e;

// rav1e_version_full() returns the full rav1e version string.
echo (string) Librav1e::rav1e_version_full() . PHP_EOL; // e.g. 0.8.1 ()

// rav1e_status_to_str() turns a status code into a readable message.
echo (string) Librav1e::rav1e_status_to_str(0) . PHP_EOL; // Normal operation
```
