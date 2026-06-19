# libleveldb/libleveldb examples

```php
use Pnlx\Libleveldb\Libleveldb;
use function Pnlx\Util\is_null;

// Open a LevelDB database, write a key, read it back, then close. The char**
// error and size_t* value-length out-parameters are plain variables by reference.
$options = Libleveldb::leveldb_options_create();
Libleveldb::leveldb_options_set_create_if_missing($options, 1);
$err = null;
$db = Libleveldb::leveldb_open($options, '/tmp/pnl-test-leveldb', $err);
if (is_null($db)) {
    throw new \RuntimeException('leveldb_open failed: ' . ($err ?? 'unknown'));
}
$wopts = Libleveldb::leveldb_writeoptions_create();
Libleveldb::leveldb_put($db, $wopts, 'hello', 5, 'world', 5, $err);
$ropts = Libleveldb::leveldb_readoptions_create();
$vlen = 0;
$val = Libleveldb::leveldb_get($db, $ropts, 'hello', 5, $vlen, $err);
echo $val . PHP_EOL; // "world"

Libleveldb::leveldb_close($db);
```
