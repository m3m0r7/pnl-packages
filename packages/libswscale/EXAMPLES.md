# libswscale/libswscale examples

```php
use Pnlx\Libswscale\Libswscale;
use function Pnlx\Util\is_null;

$libswscale = new Libswscale();

// Print the libswscale version and license.
echo $libswscale->swscale_version() . PHP_EOL;
echo $libswscale->swscale_license() . PHP_EOL;

// Allocate a scaling context (640x480 YUV420P -> 1280x720 RGB24).
// AV_PIX_FMT_YUV420P=0, AV_PIX_FMT_RGB24=2, SWS_BILINEAR=2.
$ctx = $libswscale->sws_getContext(640, 480, 0, 1280, 720, 2, 2, null, null, null);
// if (!is_null($ctx)) { /* sws_scale(...) */ $libswscale->sws_freeContext($ctx); }
```
