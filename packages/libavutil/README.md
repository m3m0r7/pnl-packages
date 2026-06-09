# FFmpeg libavutil Package

Package: `libavutil/libavutil`

Base library: FFmpeg libavutil

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libavutil
```

The package requires FFmpeg libavutil headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libavutil` finishes — it comes from the package's `examples` field in `pnlx.json`.
