# libmaxminddb/libmaxminddb examples

```php
use Pnlx\Libmaxminddb\Libmaxminddb;

$libmaxminddb = new Libmaxminddb();

// MMDB_lib_version() returns the libmaxminddb version string.
$version = $libmaxminddb->MMDB_lib_version();
echo "libmaxminddb: $version\n";

// Explore further: MMDB_open(), MMDB_lookup_string(),
// MMDB_get_value(), MMDB_close(), ...
```
