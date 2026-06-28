# libmsgpack/libmsgpack version components

Read the major, minor, and revision numbers of the linked msgpack-c library as separate integers.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmsgpack\Libmsgpack;

// Each call returns one numeric component of the library version.
$maj = Libmsgpack::msgpack_version_major();
$min = Libmsgpack::msgpack_version_minor();
$rev = Libmsgpack::msgpack_version_revision();

echo "major=" . (is_object($maj) ? $maj->toInt() : $maj) . "\n";
echo "minor=" . (is_object($min) ? $min->toInt() : $min) . "\n";
echo "revision=" . (is_object($rev) ? $rev->toInt() : $rev) . "\n";
```
