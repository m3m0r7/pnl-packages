# libfido2/libfido2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfido2\Libfido2;

// fido_strerr() maps a libfido2 status code to its message string.
echo Libfido2::fido_strerr(0) . PHP_EOL; // "FIDO_ERR_SUCCESS"
```
