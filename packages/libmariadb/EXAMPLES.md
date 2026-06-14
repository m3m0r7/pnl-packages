# libmariadb/libmariadb examples

```php
use Pnlx\Libmariadb\Libmariadb;
use function Pnlx\Util\is_null;

$libmariadb = new Libmariadb();

// Connect to MariaDB, run a query, fetch a row, then close.
$info = $libmariadb->mysql_get_client_info(); // returns string
echo 'Client: ' . $info . PHP_EOL;
$conn = $libmariadb->mysql_init(null);
if (is_null($conn)) {
    throw new \RuntimeException('mysql_init failed');
}
$handle = $libmariadb->mysql_real_connect(
    $conn, '127.0.0.1', 'root', '', 'test', 3306, null, 0
);
$libmariadb->mysql_query($conn, 'SELECT VERSION()');
$result = $libmariadb->mysql_store_result($conn);
$libmariadb->mysql_free_result($result);
$libmariadb->mysql_close($conn);
```
