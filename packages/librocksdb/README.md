# RocksDB Package

Package: `librocksdb/librocksdb`

Base library: RocksDB

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/librocksdb
```

The package requires RocksDB headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Librocksdb\Librocksdb;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$librocksdb = $runtime->load(Librocksdb::class);

// Open a RocksDB database
$opts = $librocksdb->rocksdb_options_create();
$librocksdb->rocksdb_options_set_create_if_missing($opts, 1);
$err = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$db = $librocksdb->rocksdb_open($opts, '/tmp/myrocksdb', $err);
if (is_null($db)) {
    throw new \RuntimeException('rocksdb_open failed');
}

// Write and read a key
$wopts = $librocksdb->rocksdb_writeoptions_create();
$librocksdb->rocksdb_put($db, $wopts, 'hello', 5, 'world', 5, $err);
$ropts = $librocksdb->rocksdb_readoptions_create();
$vlen  = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$val   = $librocksdb->rocksdb_get($db, $ropts, 'hello', 5, $vlen, $err);
echo "hello => {$val}\n";

$librocksdb->rocksdb_close($db);
$librocksdb->rocksdb_options_destroy($opts);
```

This snippet is printed when `pnl install librocksdb` finishes — it comes from the package's `examples` field in `pnlx.json`.
