# FFmpeg libavformat Package

Package: `libavformat/libavformat`

Base library: FFmpeg libavformat

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libavformat
```

The package requires FFmpeg libavformat headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libavformat\Libavformat;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libavformat = $runtime->load(Libavformat::class);

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

This snippet is printed when `pnl install libavformat` finishes — it comes from the package's `examples` field in `pnlx.json`.
