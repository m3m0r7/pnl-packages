# SQLite3 Package

Package: `libsqlite3/libsqlite3`

Base library: SQLite3

License: blessing

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsqlite3
```

The package requires SQLite3 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsqlite3\Libsqlite3;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libsqlite3 = $runtime->load(Libsqlite3::class);

echo $libsqlite3->sqlite3_libversion() . PHP_EOL;

// Open an in-memory database.
$dbPtr = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = $libsqlite3->sqlite3_open(':memory:', $dbPtr);
if ($rc !== 0) { throw new \RuntimeException('sqlite3_open failed: ' . $rc); }
$db = $dbPtr[0];
$libsqlite3->sqlite3_exec($db, 'CREATE TABLE t (id INTEGER PRIMARY KEY, val TEXT)', null, null, null);
$libsqlite3->sqlite3_close($db);
```

This snippet is printed when `pnl install libsqlite3` finishes — it comes from the package's `examples` field in `pnlx.json`.
