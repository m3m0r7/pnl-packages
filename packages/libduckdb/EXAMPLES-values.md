# libduckdb/libduckdb value boxing

Box PHP scalars into opaque `duckdb_value` handles with `duckdb_create_*` and read them back with the matching `duckdb_get_*`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libduckdb\Libduckdb;

// Round-trip scalar values through DuckDB's duckdb_value boxing API:
// duckdb_create_* boxes a PHP scalar into an opaque duckdb_value, and the
// matching duckdb_get_* reads it straight back out again.
$d = Libduckdb::duckdb_create_double(3.5);
$num = Libduckdb::duckdb_get_double($d);
echo 'double round-trip: ' . (string) $num . PHP_EOL;

$s = Libduckdb::duckdb_create_varchar('hello duckdb');
$text = Libduckdb::duckdb_get_varchar($s);
echo 'varchar round-trip: ' . (string) $text . PHP_EOL;

$b = Libduckdb::duckdb_create_bool(1);
$flag = Libduckdb::duckdb_get_bool($b);
echo 'bool round-trip: ' . (string) $flag . PHP_EOL;
```
