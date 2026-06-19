# libavformat/libavformat examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libavformat\Libavformat;

// Print the libavformat version and configuration
$version = Libavformat::avformat_version()->toInt();
$major   = ($version >> 16) & 0xff;
$minor   = ($version >>  8) & 0xff;
$micro   = $version & 0xff;
echo "libavformat version: {$major}.{$minor}.{$micro}\n";

$config = Libavformat::avformat_configuration();
echo "Configuration: {$config}\n";

// Open a media file: Libavformat::avformat_open_input($ctx, 'video.mp4', null, null)
// then Libavformat::avformat_find_stream_info($ctx, null)
```
