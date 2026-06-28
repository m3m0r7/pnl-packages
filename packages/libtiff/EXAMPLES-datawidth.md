# libtiff/libtiff tag data-type widths

Use TIFFDataWidth() as a pure lookup that returns the byte width of a TIFF tag data type.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtiff\Libtiff;

use const Pnlx\Libtiff\TIFF_SHORT;
use const Pnlx\Libtiff\TIFF_LONG;
use const Pnlx\Libtiff\TIFF_RATIONAL;

// TIFFDataWidth() is a pure lookup: it returns the byte width of a TIFF tag
// data type. The TIFFDataType values are generated constants.
foreach (['TIFF_SHORT' => TIFF_SHORT, 'TIFF_LONG' => TIFF_LONG, 'TIFF_RATIONAL' => TIFF_RATIONAL] as $name => $type) {
    $w = Libtiff::TIFFDataWidth($type);
    echo $name . ' width: ' . (is_object($w) ? $w->toInt() : $w) . " bytes\n";
}
// TIFF_SHORT width: 2 bytes / TIFF_LONG width: 4 bytes / TIFF_RATIONAL width: 8 bytes
```
