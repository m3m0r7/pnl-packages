# libavformat/libavformat examples

```php
use Pnlx\Libavformat\Libavformat;

$libavformat = new Libavformat();

// Print the libavformat version and configuration
$version = $libavformat->avformat_version();
$major   = ($version >> 16) & 0xff;
$minor   = ($version >>  8) & 0xff;
$micro   = $version & 0xff;
echo "libavformat version: {$major}.{$minor}.{$micro}\n";

$config = $libavformat->avformat_configuration();
echo "Configuration: {$config}\n";

// Open a media file: $libavformat->avformat_open_input($ctx, 'video.mp4', null, null)
// then $libavformat->avformat_find_stream_info($ctx, null)
```
