# libleveldb/libleveldb examples

```php
use Pnlx\Libleveldb\Libleveldb;
use function Pnlx\Util\is_null;

// Open a LevelDB database, write a key, read it back, then close.
$options = Libleveldb::leveldb_options_create();
Libleveldb::leveldb_options_set_create_if_missing($options, 1);
$errPtr = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$db = Libleveldb::leveldb_open($options, '/tmp/pnl-test-leveldb', $errPtr);
$wopts = Libleveldb::leveldb_writeoptions_create();
Libleveldb::leveldb_put($db, $wopts, 'hello', 5, 'world', 5, $errPtr);
$ropts = Libleveldb::leveldb_readoptions_create();
$vlenPtr = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int64);
$val = Libleveldb::leveldb_get($db, $ropts, 'hello', 5, $vlenPtr, $errPtr);
echo $val . PHP_EOL; // "world"
Libleveldb::leveldb_close($db);
Libleveldb::leveldb_options_destroy($options);
```
