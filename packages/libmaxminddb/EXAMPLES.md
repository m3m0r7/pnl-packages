# libmaxminddb/libmaxminddb examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmaxminddb\Libmaxminddb;

// MMDB_lib_version() returns the libmaxminddb version string.
$version = Libmaxminddb::MMDB_lib_version();
echo "libmaxminddb: $version\n";

// Explore further: MMDB_open(), MMDB_lookup_string(),
// MMDB_get_value(), MMDB_close(), ...
```
