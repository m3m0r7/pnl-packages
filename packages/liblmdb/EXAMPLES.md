# liblmdb/liblmdb examples

```php
use Pnlx\Liblmdb\Liblmdb;

// Query the LMDB library version string (returns char*).
$majorPtr = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$minorPtr = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$patchPtr = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$ver = Liblmdb::mdb_version($majorPtr, $minorPtr, $patchPtr); // returns string
echo 'LMDB version: ' . $ver . PHP_EOL;
// Main entry points to explore: mdb_env_create, mdb_env_open,
// mdb_txn_begin, mdb_dbi_open, mdb_put, mdb_get, mdb_txn_commit, mdb_env_close.
```
