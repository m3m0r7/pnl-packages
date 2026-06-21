# libzimg/libzimg examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libzimg\Libzimg;

// zimg_get_version_info() writes major/minor/micro into its out-parameters.
$major = null; $minor = null; $micro = null;
Libzimg::zimg_get_version_info($major, $minor, $micro);
echo "zimg {$major}.{$minor}.{$micro}" . PHP_EOL;
```
