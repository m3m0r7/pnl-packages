# libyajl status codes

`yajl_status_to_string()` turns a numeric `yajl_status` code into a human-readable description.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libyajl\Libyajl;

// yajl_status_to_string() maps a yajl_status code to a human-readable string.
foreach ([0, 1, 2] as $code) {
    $msg = Libyajl::yajl_status_to_string($code);
    echo "status $code: " . (string)$msg . "\n";
}
```
