# libwebp/libwebp encoder version

`WebPGetEncoderVersion()` reports the version of the bundled WebP encoder packed as `(major<<16 | minor<<8 | revision)`, the encode-side counterpart to `WebPGetDecoderVersion()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libwebp\Libwebp;

// WebPGetEncoderVersion() returns the encoder version as (major<<16 | minor<<8 | revision).
$ver = Libwebp::WebPGetEncoderVersion();
$ver = is_object($ver) ? $ver->toInt() : $ver;
echo sprintf("libwebp encoder %d.%d.%d\n",
    ($ver >> 16) & 0xff, ($ver >> 8) & 0xff, $ver & 0xff);
```
