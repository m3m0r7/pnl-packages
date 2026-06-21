# libhdf5/libhdf5 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhdf5\Libhdf5;

// H5get_libversion() writes major/minor/release into its out-parameters.
$major = null; $minor = null; $release = null;
Libhdf5::H5get_libversion($major, $minor, $release);
echo "hdf5 {$major}.{$minor}.{$release}" . PHP_EOL;
```
