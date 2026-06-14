# libavif/libavif examples

```php
use Pnlx\Libavif\Libavif;
use function Pnlx\Util\is_null;

// Print the libavif version string
$version = Libavif::avifVersion();
echo "libavif version: {$version}\n";

// Decode an AVIF file
$decoder = Libavif::avifDecoderCreate();
if (is_null($decoder)) {
    throw new \RuntimeException('avifDecoderCreate failed');
}
// Libavif::avifDecoderSetIOFile($decoder, 'image.avif');
// Libavif::avifDecoderParse($decoder);
// Libavif::avifDecoderNextImage($decoder);
Libavif::avifDecoderDestroy($decoder);
```
