# libavutil/libavutil examples

```php
use Pnlx\Libavutil\Libavutil;

// Print the libavutil version string
$version = Libavutil::avutil_version();
$major   = ($version >> 16) & 0xff;
$minor   = ($version >>  8) & 0xff;
$micro   = $version & 0xff;
echo "libavutil version: {$major}.{$minor}.{$micro}\n";

// Compute a log2 value using the libavutil helper
$log2val = Libavutil::av_log2(256);
echo "av_log2(256) = {$log2val}\n"; // 8

// Rescale a timestamp: Libavutil::av_rescale_q($pts, $src_tb, $dst_tb)
```
