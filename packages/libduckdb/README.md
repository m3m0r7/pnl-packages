# DuckDB Package

Package: `libduckdb/libduckdb`

Base library: DuckDB

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libduckdb
```

The package requires DuckDB headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libduckdb\Libduckdb;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libduckdb = $runtime->load(Libduckdb::class);

// Query the DuckDB library version string.
$version = $libduckdb->duckdb_library_version();
echo "DuckDB version: " . $version . PHP_EOL;

// Open an in-memory database, connect, run a query, then close.
// duckdb_open(path, *db)  duckdb_connect(db, *con)  duckdb_query(con, sql, *result)
$allocator = $runtime->allocator();
$db     = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$con    = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$result = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libduckdb->duckdb_open(null, $db);
$libduckdb->duckdb_connect($db->cdata, $con);
$libduckdb->duckdb_query($con->cdata, "SELECT 42 AS answer", $result);
$libduckdb->duckdb_destroy_result($result);
$libduckdb->duckdb_disconnect($con);
$libduckdb->duckdb_close($db);
```

This snippet is printed when `pnl install libduckdb` finishes — it comes from the package's `examples` field in `pnlx.json`.
