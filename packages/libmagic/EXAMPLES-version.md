# libmagic version and default database path

Read the libmagic library version and the path of the default compiled magic database without opening a handle.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmagic\Libmagic;

// magic_version() returns the libmagic version as an integer (e.g. 548 == 5.48).
$version = Libmagic::magic_version();
echo 'version: ' . (is_object($version) ? $version->toInt() : $version) . PHP_EOL;

// magic_getpath(null, 0) returns the path of the default compiled magic database.
$path = Libmagic::magic_getpath(null, 0);
echo 'default database: ' . (string) $path . PHP_EOL;
```
