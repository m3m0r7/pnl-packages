# libcairo/libcairo version example

Query cairo's compile-time version (number and string) and decode a status code to human-readable text.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcairo\Libcairo;

// Query cairo's compile-time version and decode a status code to text.
$version = Libcairo::cairo_version();
echo 'cairo version: ' . (is_object($version) ? $version->toInt() : $version) . "\n";

$versionString = Libcairo::cairo_version_string();
echo 'cairo version string: ' . (string) $versionString . "\n";

// CAIRO_STATUS_SUCCESS == 0
$status = Libcairo::cairo_status_to_string(0);
echo 'cairo status 0: ' . (string) $status . "\n";
```
