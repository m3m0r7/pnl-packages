# libtiff/libtiff examples

```php
use Pnlx\Libtiff\Libtiff;
use function Pnlx\Util\is_null;

// Print the libtiff version string.
echo Libtiff::TIFFGetVersion() . PHP_EOL;

// Open a TIFF file for reading.
$tif = Libtiff::TIFFOpen('/path/to/image.tiff', 'r');
if (is_null($tif)) { throw new \RuntimeException('TIFFOpen failed'); }
// Read image width and height (TIFFTAG_IMAGEWIDTH=256, TIFFTAG_IMAGELENGTH=257).
// Libtiff::TIFFGetField($tif, 256, $widthPtr);
Libtiff::TIFFClose($tif);
```
