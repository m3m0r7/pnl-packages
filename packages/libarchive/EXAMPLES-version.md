# libarchive/libarchive version example

Query the linked libarchive's packed numeric version and its human-readable version string.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libarchive\Libarchive;

// archive_version_number() returns the packed numeric libarchive version.
$n = Libarchive::archive_version_number();
echo 'version number: ' . (is_object($n) ? $n->toInt() : $n) . PHP_EOL;

// archive_version_string() returns the human-readable libarchive version string.
echo (string) Libarchive::archive_version_string() . PHP_EOL;
```
