# libmariadb/libmariadb examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmariadb\Libmariadb;
use function Pnlx\Util\is_null;

// Connect to MariaDB, run a query, fetch a row, then close.
$info = Libmariadb::mysql_get_client_info(); // returns string
echo 'Client: ' . $info . PHP_EOL;
$conn = Libmariadb::mysql_init(null);
if (is_null($conn)) {
    throw new \RuntimeException('mysql_init failed');
}
$handle = Libmariadb::mysql_real_connect(
    $conn, '127.0.0.1', 'root', '', 'test', 3306, null, 0
);
Libmariadb::mysql_query($conn, 'SELECT VERSION()');
$result = Libmariadb::mysql_store_result($conn);
Libmariadb::mysql_free_result($result);
Libmariadb::mysql_close($conn);
```
