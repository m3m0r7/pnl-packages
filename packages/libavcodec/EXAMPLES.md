# libavcodec/libavcodec examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libavcodec\Libavcodec;

// Print the libavcodec version string
$version = Libavcodec::avcodec_version()->toInt();
$major   = ($version >> 16) & 0xff;
$minor   = ($version >>  8) & 0xff;
$micro   = $version & 0xff;
echo "libavcodec version: {$major}.{$minor}.{$micro}\n";

// List available codec configuration
$config = Libavcodec::avcodec_configuration();
echo "Configuration: {$config}\n";

// Explore codecs: Libavcodec::avcodec_find_encoder(AV_CODEC_ID_H264)
// then Libavcodec::avcodec_alloc_context3($codec)
```
