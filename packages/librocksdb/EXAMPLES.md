# librocksdb/librocksdb examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Librocksdb\Librocksdb;
use function Pnlx\Util\is_null;

// Open a RocksDB database. The char** error out-parameter and the size_t* value
// length out-parameter are passed as plain variables by reference.
$opts = Librocksdb::rocksdb_options_create();
Librocksdb::rocksdb_options_set_create_if_missing($opts, 1);
$err = null;
$db = Librocksdb::rocksdb_open($opts, '/tmp/pnl-test-rocksdb', $err);
if (is_null($db)) {
    throw new \RuntimeException('rocksdb_open failed: ' . ($err ?? 'unknown'));
}

$wopts = Librocksdb::rocksdb_writeoptions_create();
Librocksdb::rocksdb_put($db, $wopts, 'hello', 5, 'world', 5, $err);
$ropts = Librocksdb::rocksdb_readoptions_create();
$vlen  = 0;
$val   = Librocksdb::rocksdb_get($db, $ropts, 'hello', 5, $vlen, $err);
echo "hello => {$val}\n";

Librocksdb::rocksdb_close($db);
Librocksdb::rocksdb_options_destroy($opts);
```
