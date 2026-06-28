# libbz2/libbz2 version example

Query the bzip2 library's runtime version string with `BZ2_bzlibVersion()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libbz2\Libbz2;

// Query the bzip2 library's runtime version string.
$version = Libbz2::BZ2_bzlibVersion();
echo 'libbz2 version: ' . (string) $version . "\n";
```
