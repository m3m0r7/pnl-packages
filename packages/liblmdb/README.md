# LMDB Package

Package: `liblmdb/liblmdb`

Base library: LMDB

License: OLDAP-2.8

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liblmdb
```

The package requires LMDB headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Liblmdb\Liblmdb;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$liblmdb = $runtime->load(Liblmdb::class);

// Query the LMDB library version string (returns char*).
$majorPtr = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$minorPtr = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$patchPtr = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$ver = $liblmdb->mdb_version($majorPtr, $minorPtr, $patchPtr); // returns string
echo 'LMDB version: ' . $ver . PHP_EOL;
// Main entry points to explore: mdb_env_create, mdb_env_open,
// mdb_txn_begin, mdb_dbi_open, mdb_put, mdb_get, mdb_txn_commit, mdb_env_close.
```

This snippet is printed when `pnl install liblmdb` finishes — it comes from the package's `examples` field in `pnlx.json`.
