# libduktape/libduktape examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libduktape\Libduktape;
use function Pnlx\Util\is_null;

// duk_create_heap_default() is a macro for duk_create_heap(NULL, NULL, NULL, NULL, NULL).
$ctx = Libduktape::duk_create_heap(null, null, null, null, null);
echo !is_null($ctx) ? "duktape heap created\n" : "failed\n";
if (!is_null($ctx)) {
    Libduktape::duk_destroy_heap($ctx);
}
```
