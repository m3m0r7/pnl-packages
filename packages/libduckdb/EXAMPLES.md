# libduckdb/libduckdb examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libduckdb\Libduckdb;

// Query the DuckDB library version string.
$version = Libduckdb::duckdb_library_version();
echo "DuckDB version: " . $version . PHP_EOL;

// Open an in-memory database, connect, run a query, then close.
// duckdb_open(path, *db)  duckdb_connect(db, *con)  duckdb_query(con, sql, *result)
$allocator = (new \Pnlx\FFI\Allocator());
$db     = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$con    = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$result = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
Libduckdb::duckdb_open(null, $db);
Libduckdb::duckdb_connect($db->cdata, $con);
Libduckdb::duckdb_query($con->cdata, "SELECT 42 AS answer", $result);
Libduckdb::duckdb_destroy_result($result);
Libduckdb::duckdb_disconnect($con);
Libduckdb::duckdb_close($db);
```
