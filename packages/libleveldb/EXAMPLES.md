# libleveldb/libleveldb examples

```php
use Pnlx\Libleveldb\Libleveldb;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libleveldb = $runtime->load(Libleveldb::class);

// Open a LevelDB database, write a key, read it back, then close.
$options = $libleveldb->leveldb_options_create();
$libleveldb->leveldb_options_set_create_if_missing($options, 1);
$errPtr = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$db = $libleveldb->leveldb_open($options, '/tmp/pnl-test-leveldb', $errPtr);
$wopts = $libleveldb->leveldb_writeoptions_create();
$libleveldb->leveldb_put($db, $wopts, 'hello', 5, 'world', 5, $errPtr);
$ropts = $libleveldb->leveldb_readoptions_create();
$vlenPtr = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int64);
$val = $libleveldb->leveldb_get($db, $ropts, 'hello', 5, $vlenPtr, $errPtr);
echo $val . PHP_EOL; // "world"
$libleveldb->leveldb_close($db);
$libleveldb->leveldb_options_destroy($options);
```
