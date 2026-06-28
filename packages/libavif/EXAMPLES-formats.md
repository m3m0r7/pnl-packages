# libavif format and codec introspection

Convert enum and result codes to their human-readable names and discover the codec libavif selects automatically.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libavif\Libavif;

// Human-readable name for a YUV pixel format enum value.
$fmt = Libavif::avifPixelFormatToString(3); // AVIF_PIXEL_FORMAT_YUV420
echo "pixel format 3: " . (string) $fmt . "\n";

// Human-readable message for an avifResult code.
$res = Libavif::avifResultToString(0); // AVIF_RESULT_OK
echo "result 0: " . (string) $res . "\n";

// Name of the encoder/decoder codec chosen automatically.
$codec = Libavif::avifCodecName(0, 0); // AVIF_CODEC_CHOICE_AUTO, no required flags
echo "codec name: " . (string) $codec . "\n";
```
