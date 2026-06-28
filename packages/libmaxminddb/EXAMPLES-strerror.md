# libmaxminddb/libmaxminddb error messages

`MMDB_strerror()` turns a libmaxminddb status code (the value returned by `MMDB_open()`, `MMDB_lookup_string()`, `MMDB_get_value()`, ...) into a human-readable message.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmaxminddb\Libmaxminddb;

// MMDB_strerror() turns a libmaxminddb status code into a human-readable
// message, the way you would render an error after MMDB_open()/MMDB_lookup_*().
foreach ([0, 1, 7, 11] as $code) {
    $msg = Libmaxminddb::MMDB_strerror($code);
    echo "code {$code}: " . (string) $msg . "\n";
}
```
