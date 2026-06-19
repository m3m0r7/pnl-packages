# libsqlite3/libsqlite3 examples

```php
use Pnlx\Libsqlite3\Libsqlite3;

echo Libsqlite3::sqlite3_libversion() . PHP_EOL;

// sqlite3_open() writes the database handle into its sqlite3** out-parameter, and
// sqlite3_exec() writes any error message into its char** out-parameter. Pass
// plain variables by reference; the binding hands the values back.
$db = null;
$rc = Libsqlite3::sqlite3_open(':memory:', $db);
if ($rc !== 0) { throw new \RuntimeException('sqlite3_open failed: ' . $rc); }
$errmsg = null;
Libsqlite3::sqlite3_exec($db, 'CREATE TABLE t (id INTEGER PRIMARY KEY, val TEXT)', null, null, $errmsg);
if ($errmsg !== null) { echo "exec error: {$errmsg}\n"; }
Libsqlite3::sqlite3_close($db);
echo "sqlite3 ok\n";
```
