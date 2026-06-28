# libpq thread-safety and encoding lookups

`PQisthreadsafe()` plus the `pg_encoding_to_char()`/`pg_char_to_encoding()` pair are pure helpers that need no database connection.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpq\Libpq;

// PQisthreadsafe() reports whether libpq was built thread-safe (no connection needed).
$safe = Libpq::PQisthreadsafe();
$safe = is_object($safe) ? $safe->toInt() : $safe;
echo 'libpq thread-safe: ' . ($safe ? 'yes' : 'no') . "\n";

// pg_encoding_to_char() maps a PostgreSQL encoding id to its canonical name.
$name = Libpq::pg_encoding_to_char(6); // PG_UTF8 = 6
echo 'encoding 6 = ' . (string) $name . "\n";

// pg_char_to_encoding() is the inverse, mapping a name back to its id.
$id = Libpq::pg_char_to_encoding('UTF8');
$id = is_object($id) ? $id->toInt() : $id;
echo "UTF8 id = {$id}\n";
```
