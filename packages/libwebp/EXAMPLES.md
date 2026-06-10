# libwebp/libwebp examples

```php
use Pnlx\Libwebp\Libwebp;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libwebp = $runtime->load(Libwebp::class);

// WebPGetDecoderVersion() returns version as (major<<16|minor<<8|revision).
$ver = $libwebp->WebPGetDecoderVersion();
echo sprintf("libwebp decoder %d.%d.%d\n",
    ($ver >> 16) & 0xff, ($ver >> 8) & 0xff, $ver & 0xff);

// Explore further: WebPDecodeRGBA(), WebPEncodeRGB(), WebPGetInfo(), ...
```
