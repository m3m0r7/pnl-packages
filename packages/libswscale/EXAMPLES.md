# libswscale/libswscale examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libswscale\Libswscale;
use function Pnlx\Util\is_null;

// Print the libswscale version and license.
echo Libswscale::swscale_version() . PHP_EOL;
echo Libswscale::swscale_license() . PHP_EOL;

// Allocate a scaling context (640x480 YUV420P -> 1280x720 RGB24).
// AV_PIX_FMT_YUV420P=0, AV_PIX_FMT_RGB24=2, SWS_BILINEAR=2.
$ctx = Libswscale::sws_getContext(640, 480, 0, 1280, 720, 2, 2, null, null, null);
// if (!is_null($ctx)) { /* sws_scale(...) */ Libswscale::sws_freeContext($ctx); }
```
