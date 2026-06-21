# libmatio/libmatio examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmatio\Libmatio;

// Mat_GetLibraryVersion() writes major/minor/release into its out-parameters.
$major = null; $minor = null; $release = null;
Libmatio::Mat_GetLibraryVersion($major, $minor, $release);
echo "matio {$major}.{$minor}.{$release}" . PHP_EOL;
```
