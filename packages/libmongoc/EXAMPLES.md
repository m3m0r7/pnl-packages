# libmongoc/libmongoc examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmongoc\Libmongoc;

// mongoc_init() must run once before any other driver call.
Libmongoc::mongoc_init();
$version = Libmongoc::mongoc_get_version();
echo "libmongoc: $version\n";
Libmongoc::mongoc_cleanup();

// Explore further: mongoc_client_new(), mongoc_client_get_collection(),
// mongoc_collection_insert_one(), mongoc_collection_find_with_opts(), ...
```
