# MariaDB Connector/C Package

Package: `libmariadb/libmariadb`

Base library: MariaDB Connector/C

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmariadb
```

The package requires MariaDB Connector/C headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmariadb\Libmariadb;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libmariadb = $runtime->load(Libmariadb::class);

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

This snippet is printed when `pnl install libmariadb` finishes — it comes from the package's `examples` field in `pnlx.json`.
