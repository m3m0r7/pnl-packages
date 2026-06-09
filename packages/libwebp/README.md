# libwebp Package

Package: `libwebp/libwebp`

Base library: libwebp

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libwebp
```

The package requires libwebp headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libwebp\Libwebp;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libwebp = $runtime->load(Libwebp::class);

// WebPGetDecoderVersion() returns version as (major<<16|minor<<8|revision).
$ver = $libwebp->WebPGetDecoderVersion();
echo sprintf("libwebp decoder %d.%d.%d\n",
    ($ver >> 16) & 0xff, ($ver >> 8) & 0xff, $ver & 0xff);

// Explore further: WebPDecodeRGBA(), WebPEncodeRGB(), WebPGetInfo(), ...
```

This snippet is printed when `pnl install libwebp` finishes — it comes from the package's `examples` field in `pnlx.json`.
