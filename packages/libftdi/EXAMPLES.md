# libftdi/libftdi examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libftdi\Libftdi;
use function Pnlx\Util\is_null;

// ftdi_new() allocates and initialises a context (no device needed); free it again.
$ctx = Libftdi::ftdi_new();
echo !is_null($ctx) ? "ftdi context created\n" : "ftdi_new() failed\n";
if (!is_null($ctx)) {
    Libftdi::ftdi_free($ctx);
}
```
