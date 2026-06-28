# libswscale/libswscale pixel-format support

Report the build configuration and probe whether given pixel formats are usable as scaler input/output.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libswscale\Libswscale;

// Build/configuration flags this libswscale was compiled with.
echo (string) Libswscale::swscale_configuration() . PHP_EOL;

// Query whether a pixel format is supported as scaler input/output.
// AV_PIX_FMT_YUV420P=0, AV_PIX_FMT_RGB24=2.
$in = Libswscale::sws_isSupportedInput(0);
$out = Libswscale::sws_isSupportedOutput(2);
echo 'YUV420P input supported: ' . (is_object($in) ? $in->toInt() : $in) . PHP_EOL;
echo 'RGB24 output supported: ' . (is_object($out) ? $out->toInt() : $out) . PHP_EOL;
```
