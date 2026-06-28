# libavcodec license and codec names

Read the build's license string with `avcodec_license()` and resolve `AVCodecID` values to short codec names with `avcodec_get_name()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libavcodec\Libavcodec;

// The license under which this libavcodec build was compiled.
echo 'License: ' . (string)Libavcodec::avcodec_license() . "\n";

// Resolve codec IDs (from FFmpeg's stable AVCodecID enum) to short names.
$codecIds = [
    'H.264' => 27,    // AV_CODEC_ID_H264
    'AAC'   => 86018, // AV_CODEC_ID_AAC
    'MP3'   => 86017, // AV_CODEC_ID_MP3
];
foreach ($codecIds as $label => $id) {
    $name = Libavcodec::avcodec_get_name($id);
    echo "{$label} codec name: " . (string)$name . "\n";
}
```
