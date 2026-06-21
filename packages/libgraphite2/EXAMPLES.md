# libgraphite2/libgraphite2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgraphite2\Libgraphite2;

// gr_engine_version() writes major/minor/bugfix into its out-parameters.
$major = null; $minor = null; $bugfix = null;
Libgraphite2::gr_engine_version($major, $minor, $bugfix);
echo "graphite2 {$major}.{$minor}.{$bugfix}" . PHP_EOL;
```
