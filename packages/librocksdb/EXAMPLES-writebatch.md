# librocksdb/librocksdb WriteBatch staging

Stage put/delete operations in an in-memory WriteBatch and inspect the pending operation count before committing to any database.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Librocksdb\Librocksdb;

// Stage writes in an in-memory WriteBatch and inspect how many operations are
// pending before committing them to any database. rocksdb_writebatch_count()
// reports the number of buffered put/delete operations.
$wb = Librocksdb::rocksdb_writebatch_create();
Librocksdb::rocksdb_writebatch_put($wb, 'alpha', 5, 'one', 3);
Librocksdb::rocksdb_writebatch_put($wb, 'beta', 4, 'two', 3);
Librocksdb::rocksdb_writebatch_delete($wb, 'gamma', 5);

$count = Librocksdb::rocksdb_writebatch_count($wb);
echo 'pending operations: ' . (is_object($count) ? $count->toInt() : $count) . "\n";

Librocksdb::rocksdb_writebatch_clear($wb);
$count = Librocksdb::rocksdb_writebatch_count($wb);
echo 'after clear: ' . (is_object($count) ? $count->toInt() : $count) . "\n";

Librocksdb::rocksdb_writebatch_destroy($wb);
echo "WriteBatch destroyed\n";
```
