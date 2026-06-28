# libjxl encoder version and quality mapping

Query the encoder build and convert a JPEG-style quality value into the Butteraugli distance libjxl encodes against, all without creating an encoder.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libjxl\Libjxl;

// JxlEncoderVersion() reports the encoder library version as a packed integer.
$enc = Libjxl::JxlEncoderVersion();
$enc = is_object($enc) ? $enc->toInt() : $enc;
echo "encoder version code: $enc\n";

// JxlEncoderDistanceFromQuality() maps a JPEG-style quality (0-100) onto the
// Butteraugli distance the encoder uses internally.
$dist = Libjxl::JxlEncoderDistanceFromQuality(90.0);
$dist = is_object($dist) ? $dist->toFloat() : $dist;
echo 'distance for quality 90: ' . $dist . "\n";

$dist2 = Libjxl::JxlEncoderDistanceFromQuality(50.0);
$dist2 = is_object($dist2) ? $dist2->toFloat() : $dist2;
echo 'distance for quality 50: ' . $dist2 . "\n";
```
