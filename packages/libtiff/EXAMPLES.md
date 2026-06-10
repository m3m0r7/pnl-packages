# libtiff/libtiff examples

```php
use Pnlx\Libtiff\Libtiff;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libtiff = $runtime->load(Libtiff::class);

// Print the libtiff version string.
echo $libtiff->TIFFGetVersion() . PHP_EOL;

// Open a TIFF file for reading.
$tif = $libtiff->TIFFOpen('/path/to/image.tiff', 'r');
if (is_null($tif)) { throw new \RuntimeException('TIFFOpen failed'); }
// Read image width and height (TIFFTAG_IMAGEWIDTH=256, TIFFTAG_IMAGELENGTH=257).
// $libtiff->TIFFGetField($tif, 256, $widthPtr);
$libtiff->TIFFClose($tif);
```
