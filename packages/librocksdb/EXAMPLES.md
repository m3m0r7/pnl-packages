# librocksdb/librocksdb examples

```php
use Pnlx\Librocksdb\Librocksdb;
use function Pnlx\Util\is_null;

$librocksdb = new Librocksdb();

// Open a RocksDB database
$opts = $librocksdb->rocksdb_options_create();
$librocksdb->rocksdb_options_set_create_if_missing($opts, 1);
$err = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$db = $librocksdb->rocksdb_open($opts, '/tmp/myrocksdb', $err);
if (is_null($db)) {
    throw new \RuntimeException('rocksdb_open failed');
}

// Write and read a key
$wopts = $librocksdb->rocksdb_writeoptions_create();
$librocksdb->rocksdb_put($db, $wopts, 'hello', 5, 'world', 5, $err);
$ropts = $librocksdb->rocksdb_readoptions_create();
$vlen  = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$val   = $librocksdb->rocksdb_get($db, $ropts, 'hello', 5, $vlen, $err);
echo "hello => {$val}\n";

$librocksdb->rocksdb_close($db);
$librocksdb->rocksdb_options_destroy($opts);
```
