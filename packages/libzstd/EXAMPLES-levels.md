# libzstd/libzstd compression levels

Query the library version number and the supported compression-level range without compressing any data.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libzstd\Libzstd;

// ZSTD_versionNumber() returns the version as a single integer (MAJOR*10000 + MINOR*100 + RELEASE).
$num = Libzstd::ZSTD_versionNumber();
echo "Version number: $num\n";

// The library exposes the range of supported compression levels.
$min = Libzstd::ZSTD_minCLevel();
$max = Libzstd::ZSTD_maxCLevel();
$default = Libzstd::ZSTD_defaultCLevel();
echo "Compression levels: min=$min, default=$default, max=$max\n";
```
