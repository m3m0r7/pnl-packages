# libleveldb/libleveldb version query

Read the linked LevelDB library version with the no-argument `leveldb_major_version` and `leveldb_minor_version` calls, without opening a database.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libleveldb\Libleveldb;

// Query the linked LevelDB library version without opening a database.
$major = Libleveldb::leveldb_major_version();
$minor = Libleveldb::leveldb_minor_version();
$major = is_object($major) ? $major->toInt() : $major;
$minor = is_object($minor) ? $minor->toInt() : $minor;
echo "LevelDB version: {$major}.{$minor}" . PHP_EOL; // e.g. "LevelDB version: 1.23"
```
