# libmicrohttpd/libmicrohttpd examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmicrohttpd\Libmicrohttpd;

// Query the libmicrohttpd runtime version string.
$ver = Libmicrohttpd::MHD_get_version(); // returns string, e.g. "0.9.77"
echo 'libmicrohttpd version: ' . $ver . PHP_EOL;
// Main entry point to explore: MHD_start_daemon() -- starts an embedded HTTP
// server on a given port with a request-handler callback, returns MHD_Daemon*.
```
