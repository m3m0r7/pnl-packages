# liblcms2/liblcms2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblcms2\Liblcms2;

// cmsGetEncodedCMMversion() returns the Little-CMS version encoded as MMmm0.
$v = Liblcms2::cmsGetEncodedCMMversion()->toInt();
printf("lcms2 %.2f\n", $v / 1000);
```
