# libcfitsio/libcfitsio examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcfitsio\Libcfitsio;

// ffvers() writes the CFITSIO version into its float out-parameter.
$version = 0.0;
Libcfitsio::ffvers($version);
printf("cfitsio %.3f\n", $version);
```
