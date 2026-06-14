# libmicrohttpd/libmicrohttpd examples

```php
use Pnlx\Libmicrohttpd\Libmicrohttpd;

$libmicrohttpd = new Libmicrohttpd();

// Query the libmicrohttpd runtime version string.
$ver = $libmicrohttpd->MHD_get_version(); // returns string, e.g. "0.9.77"
echo 'libmicrohttpd version: ' . $ver . PHP_EOL;
// Main entry point to explore: MHD_start_daemon() -- starts an embedded HTTP
// server on a given port with a request-handler callback, returns MHD_Daemon*.
```
