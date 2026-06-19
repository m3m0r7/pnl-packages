# libxxhash/libxxhash examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libxxhash\Libxxhash;

// XXH_versionNumber() returns version as (major*100*100 + minor*100 + patch).
$ver = Libxxhash::XXH_versionNumber()->toInt();
echo sprintf("xxHash %d.%d.%d\n",
    intdiv($ver, 10000), intdiv($ver % 10000, 100), $ver % 100);

// Explore further: XXH32(), XXH64(), XXH3_64bits(), XXH3_128bits(), ...
```
