# libavif/libavif examples

```php
use Pnlx\Libavif\Libavif;
use function Pnlx\Util\is_null;

$libavif = new Libavif();

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
