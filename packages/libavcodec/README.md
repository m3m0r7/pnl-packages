# FFmpeg libavcodec Package

Package: `libavcodec/libavcodec`

Base library: FFmpeg libavcodec

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libavcodec
```

The package requires FFmpeg libavcodec headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libavcodec\Libavcodec;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libavcodec = $runtime->load(Libavcodec::class);

// Print the libavcodec version string
$version = $libavcodec->avcodec_version();
$major   = ($version >> 16) & 0xff;
$minor   = ($version >>  8) & 0xff;
$micro   = $version & 0xff;
echo "libavcodec version: {$major}.{$minor}.{$micro}\n";

// List available codec configuration
$config = $libavcodec->avcodec_configuration();
echo "Configuration: {$config}\n";

// Explore codecs: $libavcodec->avcodec_find_encoder(AV_CODEC_ID_H264)
// then $libavcodec->avcodec_alloc_context3($codec)
```

This snippet is printed when `pnl install libavcodec` finishes — it comes from the package's `examples` field in `pnlx.json`.
