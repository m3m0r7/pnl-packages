# libpq/libpq examples

```php
use Pnlx\Libpq\Libpq;
use function Pnlx\Util\is_null;

$libpq = new Libpq();

// Connect to a PostgreSQL database
$conn = $libpq->PQconnectdb('host=127.0.0.1 dbname=mydb user=postgres password=secret');
if (is_null($conn) || $libpq->PQstatus($conn) !== 0) { // CONNECTION_OK = 0
    throw new \RuntimeException('PQconnectdb failed: ' . $libpq->PQerrorMessage($conn));
}

// Execute a query
$res = $libpq->PQexec($conn, 'SELECT version()');
if ($libpq->PQresultStatus($res) === 1) { // PGRES_TUPLES_OK = 1 (but use constant when available)
    echo $libpq->PQgetvalue($res, 0, 0) . "\n";
}
$libpq->PQclear($res);
$libpq->PQfinish($conn);
```
