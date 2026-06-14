# libpq/libpq examples

```php
use Pnlx\Libpq\Libpq;
use function Pnlx\Util\is_null;

// Connect to a PostgreSQL database
$conn = Libpq::PQconnectdb('host=127.0.0.1 dbname=mydb user=postgres password=secret');
if (is_null($conn) || Libpq::PQstatus($conn) !== 0) { // CONNECTION_OK = 0
    throw new \RuntimeException('PQconnectdb failed: ' . Libpq::PQerrorMessage($conn));
}

// Execute a query
$res = Libpq::PQexec($conn, 'SELECT version()');
if (Libpq::PQresultStatus($res) === 1) { // PGRES_TUPLES_OK = 1 (but use constant when available)
    echo Libpq::PQgetvalue($res, 0, 0) . "\n";
}
Libpq::PQclear($res);
Libpq::PQfinish($conn);
```
