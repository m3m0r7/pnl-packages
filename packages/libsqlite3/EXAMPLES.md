# libsqlite3/libsqlite3 examples

```php
use Pnlx\Libsqlite3\Libsqlite3;
use function Pnlx\Util\is_null;

echo Libsqlite3::sqlite3_libversion() . PHP_EOL;

// Open an in-memory database.
$dbPtr = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = Libsqlite3::sqlite3_open(':memory:', $dbPtr);
if ($rc !== 0) { throw new \RuntimeException('sqlite3_open failed: ' . $rc); }
$db = $dbPtr[0];
Libsqlite3::sqlite3_exec($db, 'CREATE TABLE t (id INTEGER PRIMARY KEY, val TEXT)', null, null, null);
Libsqlite3::sqlite3_close($db);
```
