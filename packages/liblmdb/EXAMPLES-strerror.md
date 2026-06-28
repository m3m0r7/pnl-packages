# liblmdb/liblmdb error messages

Turn LMDB result codes into human-readable strings with `mdb_strerror`, which also handles standard system errno values.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblmdb\Liblmdb;

// mdb_strerror() turns an LMDB result code into a human-readable message.
// -30798 = MDB_NOTFOUND, -30799 = MDB_KEYEXIST, 2 = ENOENT (system errno).
foreach ([-30798, -30799, 2] as $code) {
    $msg = Liblmdb::mdb_strerror($code);
    echo "{$code}: " . (string) $msg . PHP_EOL;
}
// -30798: MDB_NOTFOUND: No matching key/data pair found
// -30799: MDB_KEYEXIST: Key/data pair already exists
// 2: No such file or directory
```
