# liblmdb/liblmdb examples

```php
use Pnlx\Liblmdb\Liblmdb;

// mdb_version() returns the version string and fills three int out-parameters.
// Pass plain variables by reference; the binding writes the components back.
$major = 0;
$minor = 0;
$patch = 0;
$ver = Liblmdb::mdb_version($major, $minor, $patch); // returns string
echo 'LMDB version: ' . $ver . " ({$major}.{$minor}.{$patch})" . PHP_EOL;
// Main entry points to explore: mdb_env_create, mdb_env_open,
// mdb_txn_begin, mdb_dbi_open, mdb_put, mdb_get, mdb_txn_commit, mdb_env_close.
```
