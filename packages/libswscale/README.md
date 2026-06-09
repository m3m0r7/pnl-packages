# FFmpeg libswscale Package

Package: `libswscale/libswscale`

Base library: FFmpeg libswscale

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libswscale
```

The package requires FFmpeg libswscale headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libswscale\Libswscale;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libswscale = $runtime->load(Libswscale::class);

// Print the libswscale version and license.
echo $libswscale->swscale_version() . PHP_EOL;
echo $libswscale->swscale_license() . PHP_EOL;

// Allocate a scaling context (640x480 YUV420P -> 1280x720 RGB24).
// AV_PIX_FMT_YUV420P=0, AV_PIX_FMT_RGB24=2, SWS_BILINEAR=2.
$ctx = $libswscale->sws_getContext(640, 480, 0, 1280, 720, 2, 2, null, null, null);
// if (!is_null($ctx)) { /* sws_scale(...) */ $libswscale->sws_freeContext($ctx); }
```

This snippet is printed when `pnl install libswscale` finishes — it comes from the package's `examples` field in `pnlx.json`.
