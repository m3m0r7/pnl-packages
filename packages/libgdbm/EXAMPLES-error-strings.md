# libgdbm error messages

Translate GDBM error codes into human-readable messages with gdbm_strerror().

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgdbm\Libgdbm;

// gdbm_strerror() maps a GDBM error code to a human-readable message
// (0 = no error, and a few representative failure codes).
foreach ([0, 1, 3] as $code) {
    echo "code {$code}: " . (string)Libgdbm::gdbm_strerror($code) . PHP_EOL;
}
```
