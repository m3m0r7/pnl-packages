# libavutil/libavutil examples

```php
use Pnlx\Libavutil\Libavutil;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libavutil = $runtime->load(Libavutil::class);

// Print the libavutil version string
$version = $libavutil->avutil_version();
$major   = ($version >> 16) & 0xff;
$minor   = ($version >>  8) & 0xff;
$micro   = $version & 0xff;
echo "libavutil version: {$major}.{$minor}.{$micro}\n";

// Compute a log2 value using the libavutil helper
$log2val = $libavutil->av_log2(256);
echo "av_log2(256) = {$log2val}\n"; // 8

// Rescale a timestamp: $libavutil->av_rescale_q($pts, $src_tb, $dst_tb)
```
