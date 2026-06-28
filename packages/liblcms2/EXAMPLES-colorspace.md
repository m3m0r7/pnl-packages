# liblcms2/liblcms2 color space channels

`cmsChannelsOfColorSpace()` reports how many channels a given color space signature uses (RGB=3, CMYK=4, Gray=1).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblcms2\Liblcms2;
use Pnlx\Liblcms2\Enums\cmsColorSpaceSignature;

foreach (['RGB' => cmsColorSpaceSignature::cmsSigRgbData,
          'CMYK' => cmsColorSpaceSignature::cmsSigCmykData,
          'Gray' => cmsColorSpaceSignature::cmsSigGrayData] as $name => $sig) {
    $n = Liblcms2::cmsChannelsOfColorSpace($sig->value);
    $n = is_object($n) ? $n->toInt() : $n;
    echo "$name channels: $n" . PHP_EOL;
}
```
