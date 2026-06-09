# libavif Package

Package: `libavif/libavif`

Base library: libavif

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libavif
```

The package requires libavif headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libavif\Libavif;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libavif = $runtime->load(Libavif::class);

// Print the libavif version string
$version = $libavif->avifVersion();
echo "libavif version: {$version}\n";

// Decode an AVIF file
$decoder = $libavif->avifDecoderCreate();
if (is_null($decoder)) {
    throw new \RuntimeException('avifDecoderCreate failed');
}
// $libavif->avifDecoderSetIOFile($decoder, 'image.avif');
// $libavif->avifDecoderParse($decoder);
// $libavif->avifDecoderNextImage($decoder);
$libavif->avifDecoderDestroy($decoder);
```

This snippet is printed when `pnl install libavif` finishes — it comes from the package's `examples` field in `pnlx.json`.
