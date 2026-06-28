# libsqlite3/libsqlite3 build-info examples

A second example exercising the no-argument build/configuration queries, distinct
from the database workflow in `EXAMPLES.md`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsqlite3\Libsqlite3;

// The numeric version, encoded as (major*1_000_000 + minor*1_000 + patch).
echo 'version number: ' . Libsqlite3::sqlite3_libversion_number()->toInt() . "\n";

// The exact source check-in this build came from.
echo 'source id: ' . Libsqlite3::sqlite3_sourceid() . "\n";

// Whether the library was compiled thread-safe (non-zero = yes).
echo 'threadsafe: ' . Libsqlite3::sqlite3_threadsafe()->toInt() . "\n";
```
