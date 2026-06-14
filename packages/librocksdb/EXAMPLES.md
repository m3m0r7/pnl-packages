# librocksdb/librocksdb examples

```php
use Pnlx\Librocksdb\Librocksdb;
use function Pnlx\Util\is_null;

// Open a RocksDB database
$opts = Librocksdb::rocksdb_options_create();
Librocksdb::rocksdb_options_set_create_if_missing($opts, 1);
$err = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$db = Librocksdb::rocksdb_open($opts, '/tmp/myrocksdb', $err);
if (is_null($db)) {
    throw new \RuntimeException('rocksdb_open failed');
}

// Write and read a key
$wopts = Librocksdb::rocksdb_writeoptions_create();
Librocksdb::rocksdb_put($db, $wopts, 'hello', 5, 'world', 5, $err);
$ropts = Librocksdb::rocksdb_readoptions_create();
$vlen  = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$val   = Librocksdb::rocksdb_get($db, $ropts, 'hello', 5, $vlen, $err);
echo "hello => {$val}\n";

Librocksdb::rocksdb_close($db);
Librocksdb::rocksdb_options_destroy($opts);
```
