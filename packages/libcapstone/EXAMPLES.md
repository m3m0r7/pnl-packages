# libcapstone/libcapstone examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcapstone\Libcapstone;

// cs_version() writes major/minor into its int out-parameters (pass plain
// variables by reference) and returns the combined version number.
$major = null;
$minor = null;
Libcapstone::cs_version($major, $minor);
echo "capstone {$major}.{$minor}" . PHP_EOL;
```
