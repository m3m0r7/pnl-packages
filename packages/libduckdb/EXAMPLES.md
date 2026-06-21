# libduckdb/libduckdb examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libduckdb\Libduckdb;

// Query the DuckDB library version string.
$version = Libduckdb::duckdb_library_version();
echo "DuckDB version: " . $version . PHP_EOL;

// Open an in-memory database, connect, run a query, then close. The `*db`, `*con`
// and `*result` parameters are out-parameters: pass a variable by reference and the
// call writes the handle back into it (no manual allocation). The handle written
// back into $db/$con is then passed straight into the next call.
$db = null;
$con = null;
$result = null;
Libduckdb::duckdb_open(null, $db);
Libduckdb::duckdb_connect($db, $con);
Libduckdb::duckdb_query($con, "SELECT 42 AS answer", $result);
Libduckdb::duckdb_destroy_result($result);
Libduckdb::duckdb_disconnect($con);
Libduckdb::duckdb_close($db);
```
