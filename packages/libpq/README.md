# libpq Package

Package: `libpq/libpq`

Base library: libpq

License: PostgreSQL

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpq
```

The package requires libpq headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libpq\Libpq;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libpq = $runtime->load(Libpq::class);

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

This snippet is printed when `pnl install libpq` finishes — it comes from the package's `examples` field in `pnlx.json`.
