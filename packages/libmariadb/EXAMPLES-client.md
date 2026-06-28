# libmariadb client version and thread safety

Inspect the MariaDB client library version and whether it was built thread-safe, without opening a connection.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmariadb\Libmariadb;

// mysql_get_client_version() returns the client library version as an integer.
$version = Libmariadb::mysql_get_client_version();
echo 'client version: ' . (is_object($version) ? $version->toInt() : $version) . PHP_EOL;

// mysql_thread_safe() reports whether the client library is thread-safe (1) or not (0).
$threadSafe = Libmariadb::mysql_thread_safe();
echo 'thread safe: ' . (is_object($threadSafe) ? $threadSafe->toInt() : $threadSafe) . PHP_EOL;
```
