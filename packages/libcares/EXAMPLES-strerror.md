# libcares/libcares — error code lookup

Translate `ARES_*` status codes into human-readable messages with `ares_strerror()` (no channel or library init required).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcares\Libcares;

// ares_strerror() maps an ARES_* status code to a human-readable message,
// returning a string. No channel or library init is required.
foreach ([0, 1, 12] as $code) {
    echo "ares_strerror({$code}) = " . (string) Libcares::ares_strerror($code) . PHP_EOL;
}
```
