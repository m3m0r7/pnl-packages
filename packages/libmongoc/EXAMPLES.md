# libmongoc/libmongoc examples

```php
use Pnlx\Libmongoc\Libmongoc;

$libmongoc = new Libmongoc();

// mongoc_init() must run once before any other driver call.
$libmongoc->mongoc_init();
$version = $libmongoc->mongoc_get_version();
echo "libmongoc: $version\n";
$libmongoc->mongoc_cleanup();

// Explore further: mongoc_client_new(), mongoc_client_get_collection(),
// mongoc_collection_insert_one(), mongoc_collection_find_with_opts(), ...
```
