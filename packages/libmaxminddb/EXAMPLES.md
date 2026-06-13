# libmaxminddb/libmaxminddb examples

```php
use Pnlx\Libmaxminddb\Libmaxminddb;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libmaxminddb = $runtime->load(Libmaxminddb::class);

// MMDB_lib_version() returns the libmaxminddb version string.
$version = $libmaxminddb->MMDB_lib_version();
echo "libmaxminddb: $version\n";

// Explore further: MMDB_open(), MMDB_lookup_string(),
// MMDB_get_value(), MMDB_close(), ...
```
